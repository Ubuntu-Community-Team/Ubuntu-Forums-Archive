---
title: "[SOLVED] Script to get list of all installed packages - ordered by time"
date: 2007-07-08
forum: General Help
---

### Post by rshetye on 2007-07-08
```

#!/usr/bin/env tcsh

cd /var/lib/dpkg/info

foreach listing (`/bin/ls -rt a*.list`)
    # echo "$listing"
    # set date = `ls -tl $listing | awk '{ print $6 $7 }'`
    set date = `ls -tl $listing | cut -d' ' -f 6,7 -s`
    # echo "$date"
    set package = `echo "$listing" | sed 's/\.list$//g'`
    # echo "$package"
    set pkginfo = `dpkg -l "$package" | tail -1`
    echo "$date $pkginfo"
end

```

currently, for testing purposes, this script uses a*.list, rather than *.list.

This script is very slow due to the continuous invocation of dpkg for each package. Any ideas on how to speed things up ? I am going to rewrite in ruby, slurp in the whole dpkg for all packges and then add in the date info based on the name of the package ? Is there a better way ?

thanks!

---

### Post by rshetye on 2007-07-12
FYI: I used ruby for slurping the data, not for its OO.

```

#!/usr/bin/env ruby

$DEBUG=true
$VERBOSE=true

=begin
Copyright: Ranjeet Shetye (ranjeet@shetye.com). 2007
Licenced under GPL-2.

1. Output must be sorted by time
2. Get the info for all installed packages from the dpkg db
3. Store this info in a hash that is indexed by the package name
4. Read the /var/lib/dpkg/info directory and get the list of all *.list files - an indication of installed packages
5. For each *.list file, the * itself is the package name. get its mtime
6. Sort this list by the mtime, use the package name to get the details from the other hash that you created earlier.
7. print it all out!!
8. ???
9. Profit!

ps: for testing purposes, use Dir.glob for q*.list rather than *.list, its easier to deal with a much shorter list

=end

class DPkgTimeOrdered
    def initialize
        @pkg_mod_time = Hash.new
        @pkg_details = Hash.new
        @dpkg_headers = Array.new
    end

    def list
        # presence of LINES and COLUMNS causes dpkg to truncate the name of the package
        ENV['LINES']=nil
        ENV['COLUMNS']=nil

        # get a list of all installed packages
        dpkg_listall = IO.popen("/usr/bin/dpkg -l", "w+")

        # eat the top 5 lines
        @dpkg_headers << "                        " + dpkg_listall.gets
        @dpkg_headers << "                        " + dpkg_listall.gets
        @dpkg_headers << "                        " + dpkg_listall.gets
        @dpkg_headers << "Install time            " + dpkg_listall.gets
        @dpkg_headers << "=======================-" + dpkg_listall.gets

        while ((pkg_details = dpkg_listall.gets) != nil)
            fields = pkg_details.split(/\s+/)
            package = fields[1]
            # TODO the IO pipe seems to truncate a line, if the description is very large. Hence pkg_details might be truncated
            @pkg_details[package] = pkg_details
        end

        Dir.chdir("/var/lib/dpkg/info");

        # TODO if a package name is provided as an argument, e.g. compiz*, then that's the pattern that we should glob
        Dir.glob("*.list").sort.each \
        { |fileentry|
            filestat=File::Stat.new(fileentry)
            package = fileentry.gsub(".list","")
            @pkg_mod_time[package] = filestat.mtime
        }

        # CANNOT just invert the array cos multiple packages might have been installed at the same time
        # Convert the hash into an array, sorted by the date, with element 1 = pkg name, and element 2 = mtime
        final_listing = @pkg_mod_time.sort { |k,v| k[1]<=>v[1] }

        puts @dpkg_headers

        final_listing.each \
        { |arr|
            puts "#{arr[1].strftime("%Y-%m-%d %H:%M:%S %Z")} #{@pkg_details[arr[0]]}"
        }
    end
end

dpto = DPkgTimeOrdered.new
dpto.list

```

---

