---
title: "CPAN won't install modules"
date: 2007-01-28
forum: General Help
---

### Post by tr333 on 2007-01-28
i'm having problems trying to install perl modules via CPAN.  whenever i try to install a module it asks to install any dependencies and then fails to install them.

example:  when i try to install Bundle::CPAN (which cpan itself tells me to do to update cpan) the modules all seem to fail on install with the same errors
```
...
Running install for module IO::Compress::Base
Running make for P/PM/PMQS/IO-Compress-Base-2.003.tar.gz
  Is already unwrapped into directory /home/tom/.cpan/build/IO-Compress-Base-2.003
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
...
```

i have no idea what could be stopping cpan from installing/compiling modules.

---

### Post by hitter on 2007-01-28
I had this same problem.. solved through this

sudo apt-get install make

this will do it.. try cpan after this

Note: u have to install gcc and some of the lib also to install many modules..

---

### Post by phossal on 2007-01-28
He's partially right. You clear up those dependencies by installing build-essential, which I'm sure you've done. It's worth double checking though, since it takes 1 second:
```
sudo apt-get install build-essential
```

More important, you need to open cpan in the terminal window using SUDO. It will need root privileges when using make:
```
sudo cpan
```

---

### Post by tr333 on 2007-01-28
i've already installed build-essential and i always run cpan with sudo, so i have no idea what could be causing cpan to do this.

---

### Post by phossal on 2007-01-28
Did you try running sudo apt-get install build-essential anyway? Sometimes, after updates, I find I need to rerun the command because things stop working.

---

### Post by tr333 on 2007-01-28
```
$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
should i try removing and reinstalling build-essential?

---

### Post by phossal on 2007-01-28
What about this one, mate?
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by tr333 on 2007-01-28
i just did a reinstall of build-essential and still not working...

when i try to install iCal::Parser::HTML it fails on installing Module::Build, which seems like some important package.

not sure if the cpan output below will help anyone understand the problem...  but it might...

```
cpan> install iCal::Parser::HTML
CPAN: Storable loaded ok
Going to read /home/tom/.cpan/Metadata
  Database was generated on Sat, 27 Jan 2007 20:26:42 GMT
Running install for module iCal::Parser::HTML
Running make for R/RF/RFRANKEL/iCal-Parser-HTML-1.06.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/tom/.cpan/sources/authors/id/R/RF/RFRANKEL/iCal-Parser-HTML-1.06.tar.gz ok
Scanning cache /home/tom/.cpan/build for sizes
iCal-Parser-HTML-1.06/
iCal-Parser-HTML-1.06/Build.PL
iCal-Parser-HTML-1.06/examples/
iCal-Parser-HTML-1.06/examples/calendar.css
iCal-Parser-HTML-1.06/examples/ical.cgi
iCal-Parser-HTML-1.06/lib/
iCal-Parser-HTML-1.06/lib/iCal/
iCal-Parser-HTML-1.06/lib/iCal/Parser/
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/cal-util.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/day-util.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/day.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/index.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/month-util.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/month.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/week.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML/stylesheet/year.xsl
iCal-Parser-HTML-1.06/lib/iCal/Parser/HTML.pm
iCal-Parser-HTML-1.06/LICENSE
iCal-Parser-HTML-1.06/Makefile.PL
iCal-Parser-HTML-1.06/MANIFEST
iCal-Parser-HTML-1.06/META.yml
iCal-Parser-HTML-1.06/README
iCal-Parser-HTML-1.06/scripts/
iCal-Parser-HTML-1.06/scripts/ical2html
iCal-Parser-HTML-1.06/t/
iCal-Parser-HTML-1.06/t/00load.t
iCal-Parser-HTML-1.06/t/01parse.t
iCal-Parser-HTML-1.06/t/calendars/
iCal-Parser-HTML-1.06/t/calendars/all-day-event.ics
iCal-Parser-HTML-1.06/t/calendars/all-day-event.ics.day.html
iCal-Parser-HTML-1.06/t/calendars/all-day-event.ics.month.html
iCal-Parser-HTML-1.06/t/calendars/all-day-event.ics.week.html
iCal-Parser-HTML-1.06/t/calendars/all-day-event.ics.year.html
iCal-Parser-HTML-1.06/t/calendars/complex.ics
iCal-Parser-HTML-1.06/t/calendars/complex.ics.day.html
iCal-Parser-HTML-1.06/t/calendars/complex.ics.month.html
iCal-Parser-HTML-1.06/t/calendars/complex.ics.week.html
iCal-Parser-HTML-1.06/t/calendars/complex.ics.year.html
iCal-Parser-HTML-1.06/t/calendars/event-duration.ics
iCal-Parser-HTML-1.06/t/calendars/event-duration.ics.day.html
iCal-Parser-HTML-1.06/t/calendars/event-duration.ics.month.html
iCal-Parser-HTML-1.06/t/calendars/event-duration.ics.week.html
iCal-Parser-HTML-1.06/t/calendars/event-duration.ics.year.html
iCal-Parser-HTML-1.06/t/calendars/multical.day.html
iCal-Parser-HTML-1.06/t/calendars/multical.month.html
iCal-Parser-HTML-1.06/t/calendars/multical.nolink.day.html
iCal-Parser-HTML-1.06/t/calendars/multical.nolink.month.html
iCal-Parser-HTML-1.06/t/calendars/multical.nolink.week.html
iCal-Parser-HTML-1.06/t/calendars/multical.week.html
iCal-Parser-HTML-1.06/t/calendars/multical.year.html
Removing previously used /home/tom/.cpan/build/iCal-Parser-HTML-1.06

  CPAN.pm: Going to build R/RF/RFRANKEL/iCal-Parser-HTML-1.06.tar.gz

This module requires Module::Build to install itself.
  Install Module::Build now from CPAN? [y]
CPAN: Storable loaded ok
Going to read /home/tom/.cpan/Metadata
  Database was generated on Sat, 27 Jan 2007 20:26:42 GMT
Running install for module Module::Build::Compat
Running make for K/KW/KWILLIAMS/Module-Build-0.2806.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/tom/.cpan/sources/authors/id/K/KW/KWILLIAMS/Module-Build-0.2806.tar.gz ok
Scanning cache /home/tom/.cpan/build for sizes
Module-Build-0.2806/
Module-Build-0.2806/Build.PL
Module-Build-0.2806/Changes
Module-Build-0.2806/contrib/
Module-Build-0.2806/contrib/bash_completion.module-build
Module-Build-0.2806/INSTALL
Module-Build-0.2806/lib/
Module-Build-0.2806/lib/Module/
Module-Build-0.2806/lib/Module/Build/
Module-Build-0.2806/lib/Module/Build/API.pod
Module-Build-0.2806/lib/Module/Build/Authoring.pod
Module-Build-0.2806/lib/Module/Build/Base.pm
Module-Build-0.2806/lib/Module/Build/Compat.pm
Module-Build-0.2806/lib/Module/Build/Config.pm
Module-Build-0.2806/lib/Module/Build/Cookbook.pm
Module-Build-0.2806/lib/Module/Build/ModuleInfo.pm
Module-Build-0.2806/lib/Module/Build/Notes.pm
Module-Build-0.2806/lib/Module/Build/Platform/
Module-Build-0.2806/lib/Module/Build/Platform/aix.pm
Module-Build-0.2806/lib/Module/Build/Platform/Amiga.pm
Module-Build-0.2806/lib/Module/Build/Platform/cygwin.pm
Module-Build-0.2806/lib/Module/Build/Platform/darwin.pm
Module-Build-0.2806/lib/Module/Build/Platform/Default.pm
Module-Build-0.2806/lib/Module/Build/Platform/EBCDIC.pm
Module-Build-0.2806/lib/Module/Build/Platform/MacOS.pm
Module-Build-0.2806/lib/Module/Build/Platform/MPEiX.pm
Module-Build-0.2806/lib/Module/Build/Platform/os2.pm
Module-Build-0.2806/lib/Module/Build/Platform/RiscOS.pm
Module-Build-0.2806/lib/Module/Build/Platform/Unix.pm
Module-Build-0.2806/lib/Module/Build/Platform/VMS.pm
Module-Build-0.2806/lib/Module/Build/Platform/VOS.pm
Module-Build-0.2806/lib/Module/Build/Platform/Windows.pm
Module-Build-0.2806/lib/Module/Build/PodParser.pm
Module-Build-0.2806/lib/Module/Build/PPMMaker.pm
Module-Build-0.2806/lib/Module/Build/Version.pm
Module-Build-0.2806/lib/Module/Build/YAML.pm
Module-Build-0.2806/lib/Module/Build.pm
Module-Build-0.2806/Makefile.PL
Module-Build-0.2806/MANIFEST
Module-Build-0.2806/META.yml
Module-Build-0.2806/README
Module-Build-0.2806/scripts/
Module-Build-0.2806/scripts/config_data
Module-Build-0.2806/SIGNATURE
Module-Build-0.2806/t/
Module-Build-0.2806/t/basic.t
Module-Build-0.2806/t/bundled/
Module-Build-0.2806/t/bundled/Test/
Module-Build-0.2806/t/bundled/Test/Builder.pm
Module-Build-0.2806/t/bundled/Test/More.pm
Module-Build-0.2806/t/bundled/Test/Simple.pm
Module-Build-0.2806/t/bundled/Tie/
Module-Build-0.2806/t/bundled/Tie/CPHash.pm
Module-Build-0.2806/t/compat.t
Module-Build-0.2806/t/destinations.t
Module-Build-0.2806/t/ext.t
Module-Build-0.2806/t/extend.t
Module-Build-0.2806/t/files.t
Module-Build-0.2806/t/install.t
Module-Build-0.2806/t/lib/
Module-Build-0.2806/t/lib/DistGen.pm
Module-Build-0.2806/t/lib/MBTest.pm
Module-Build-0.2806/t/manifypods.t
Module-Build-0.2806/t/mbyaml.t
Module-Build-0.2806/t/metadata.t
Module-Build-0.2806/t/metadata2.t
Module-Build-0.2806/t/moduleinfo.t
Module-Build-0.2806/t/notes.t
Module-Build-0.2806/t/par.t
Module-Build-0.2806/t/parents.t
Module-Build-0.2806/t/pod_parser.t
Module-Build-0.2806/t/ppm.t
Module-Build-0.2806/t/runthrough.t
Module-Build-0.2806/t/signature.t
Module-Build-0.2806/t/tilde.t
Module-Build-0.2806/t/versions.t
Module-Build-0.2806/t/xs.t
Removing previously used /home/tom/.cpan/build/Module-Build-0.2806

  CPAN.pm: Going to build K/KW/KWILLIAMS/Module-Build-0.2806.tar.gz

# running Build.PL installdirs=site
/usr/bin/perl Build.PL installdirs=site
Checking whether your kit is complete...
Looks good

Checking prerequisites...
 * Optional prerequisite Module::Signature is not installed
 * Optional prerequisite ExtUtils::ParseXS is not installed
 * Optional prerequisite version is not installed
 * Optional prerequisite Pod::Readme is not installed
 * Optional prerequisite ExtUtils::CBuilder is not installed

ERRORS/WARNINGS FOUND IN PREREQUISITES.  You may wish to install the versions
of the modules indicated above before proceeding with this installation

Checking features:
  manpage_support....enabled
  YAML_support.......disabled
    - YAML is not installed
  C_support..........disabled
    - ExtUtils::CBuilder is not installed
    * Optional prerequisite ExtUtils::ParseXS is not installed
  HTML_support.......enabled

Creating new 'Build' script for 'Module-Build' version '0.2806'
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
 *** Cannot install without Module::Build.  Exiting ...
Running make test
  Make had some problems, maybe interrupted? Won't test
Running make install
  Make had some problems, maybe interrupted? Won't install

cpan>

```

---

### Post by tr333 on 2007-01-28
> **phossal said:**
> What about this one, mate?
```
sudo apt-get install linux-headers-`uname -r`
```

installing now... :)

EDIT:  seems to do nothing to help :(

---

### Post by tr333 on 2007-01-28
from looking at my cpan output, could this be a problem from prerequisite modules not being installed? or is it some thing entirely different?

---

### Post by phossal on 2007-01-28
I wrecked my own CPAN installation testing for errors. lol The reality is that most of the modules that a person could want are in the Ubuntu repositories anyway. However, obscure modules are sometimes only available via CPAN. 

I vaguely remember using apt-get to pull a module that resolved this error in the past. I can't remember it now. I'll keep looking.

---

### Post by tr333 on 2007-01-28
thanks for your help on this...  hope we can resolve this issue.

---

### Post by tr333 on 2007-01-28
i think i've found the problem, but don't know how to fix it.  i found the information while searching google for one of the error messages given by cpan.

from the cpan prompt, typing "o conf" shows the CPAN::Config options. the entry next to 'make' is blank when i think it should contain the path to 'make'.  how do i modify the cpan config to set this?

EDIT:  is there a way to run the initial cpan config question thing?

---

### Post by phossal on 2007-01-28
```
o conf <option_name> <option_setting> 
o conf commit
```

---

### Post by phossal on 2007-01-28
I tried a bunch of settings for make, but I couldn't find a combination that worked.

---

### Post by tr333 on 2007-01-28
thanks for that.  i also found on google that "o conf init" will run the first-time initialisation.  modules seem to be installing now without failing. :D

---

### Post by phossal on 2007-01-28
Will you post your settings? My path to make is set, and it still isn't working. lol Now I desperately need *your* help.

---

### Post by tr333 on 2007-01-28
looks like i spoke too soon... :p
installing Bundle::CPAN seemed to go ok, but now trying to install iCal::Parser::HTML gives me errors.  installing the dependencies seemed to go ok for that module, but i can't tell since the terminal scrollback doesnt go far enough to see what happend.

```
Manifying blib/script/ical2html -> blib/bindoc/ical2html.1p
Manifying blib/lib/iCal/Parser/HTML.pm -> blib/libdoc/iCal::Parser::HTML.3pm
  /usr/bin/make  -- OK
Running make test
/usr/bin/perl Build --makefile_env_macros 1 test
t/00load.....
#   Failed test 'use iCal::Parser::HTML;'
#   at t/00load.t line 7.
#     Tried to use 'iCal::Parser::HTML'.
#     Error:  Can't locate iCal/Parser/SAX.pm in @INC (@INC contains: /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/lib /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/arch _build/lib /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/lib/iCal/Parser/HTML.pm line 11.
# BEGIN failed--compilation aborted at t/00load.t line 7.
# Compilation failed in require at (eval 3) line 2.
# BEGIN failed--compilation aborted at (eval 3) line 2.
Can't locate object method "new" via package "iCal::Parser::HTML" at t/00load.t line 9.
# Looks like you planned 2 tests but only ran 1.
# Looks like you failed 1 test of 1 run.
# Looks like your test died just after 1.
t/00load.....dubious
        Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 1-2
        Failed 2/2 tests, 0.00% okay
t/01parse....Can't locate iCal/Parser/SAX.pm in @INC (@INC contains: /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/lib /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/arch _build/lib /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/lib/iCal/Parser/HTML.pm line 11.
BEGIN failed--compilation aborted at /home/tom/.cpan/build/iCal-Parser-HTML-1.06/blib/lib/iCal/Parser/HTML.pm line 11.
Compilation failed in require at t/01parse.t line 3.
BEGIN failed--compilation aborted at t/01parse.t line 3.
# Looks like your test died before it could output anything.
t/01parse....dubious
        Test returned status 255 (wstat 65280, 0xff00)
Failed Test Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/00load.t   255 65280     2    3  1-2
t/01parse.t  255 65280    ??   ??  ??
Failed 2/2 test scripts. 2/2 subtests failed.
Files=2, Tests=2,  0 wallclock secs ( 0.15 cusr +  0.03 csys =  0.18 CPU)
Failed 2/2 test programs. 2/2 subtests failed.
make: *** [test] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
  RFRANKEL/iCal-Parser-HTML-1.06.tar.gz        : make_test NO
  MSERGEANT/XML-Parser-2.34.tar.gz             : make NO
  SEMANTICO/Test-XML-0.07.tar.gz               : make_test NO
  KHAMPTON/XML-SemanticDiff-0.95.tar.gz        : make_test NO


```

---

### Post by tr333 on 2007-01-28
here's my cpan conf:
```

cpan[6]> o conf
$CPAN::Config options from '/etc/perl/CPAN/Config.pm':
    commit             [Commit changes to disk]
    defaults           [Reload defaults from disk]
    help               [Short help about 'o conf' usage]
    init               [Interactive setting of all options]

    build_cache        [10]
    build_dir          [/home/tom/.cpan/build]
    cache_metadata     [1]
    commandnumber_in_prompt [1]
    cpan_home          [/home/tom/.cpan]
    dontload_hash
    ftp                [/usr/bin/ftp]
    ftp_passive        [1]
    ftp_proxy          []
    getcwd             [cwd]
    gpg                [/usr/bin/gpg]
    gzip               [/bin/gzip]
    histfile           [/home/tom/.cpan/histfile]
    histsize           [100]
    http_proxy         []
    inactivity_timeout [0]
    index_expire       [1]
    inhibit_startup_message [0]
    keep_source_where  [/home/tom/.cpan/sources]
    lynx               [/usr/bin/lynx]
    make               [/usr/bin/make]
    make_arg           []
    make_install_arg   []
    make_install_make_command [/usr/bin/make]
    makepl_arg         [INSTALLDIRS=site]
    mbuild_arg         []
    mbuild_install_arg []
    mbuild_install_build_command [sudo ./Build]
    mbuildpl_arg       []
    ncftp              [/usr/bin/ncftp]
    ncftpget           [/usr/bin/ncftpget]
    no_proxy           []
    pager              [less]
    prerequisites_policy [ask]
    scan_cache         [atstart]
    shell              [/bin/bash]
    tar                [/bin/tar]
    term_is_latin      [1]
    term_ornaments     [1]
    unzip              [/usr/bin/unzip]
    urllist
        [http://cpan.mirrors.ilisys.com.au]
    wget               [/usr/bin/wget]



```

---

### Post by phossal on 2007-01-29
I edited my personal version, in /home/phossal/.cpan/CPAN/MyConfig.pm. I had to modify a few other variables. The path to make was already set. Things seem to be working for me too, now. Thank you.

[edit] There a lot of out of date versions of the Config/MyConfig.pm out there. I was tripped up by settings in an old version.

---

### Post by phossal on 2007-01-29
You're probably about as much of an expert on this as the forums have. You should pump out a guide. :D

---

### Post by tr333 on 2007-01-29
> **phossal said:**
> I edited my personal version, in /home/phossal/.cpan/CPAN/MyConfig.pm. I had to modify a few other variables. The path to make was already set. Things seem to be working for me too, now. Thank you.

[edit] There a lot of out of date versions of the Config/MyConfig.pm out there. I was tripped up by settings in an old version.

i can't seem to find a ~/.cpan/CPAN folder. :confused:

---

### Post by ebash on 2007-01-29
Check to see if the .cpan folder wouldn't be in root's home, look for /root/.cpan/. Under some HP-UX system at work I have found many times that the .cpan folder is in root (/root/.cpan) folder or even in the root (/.cpan) of the system, perharps your .cpan was misplaced?

In a last resort try:
```
sudo updatedb; sudo locate .cpan
```

---

### Post by tr333 on 2007-01-29
the only .cpan directory is in ~/.cpan

---

### Post by gldvxx on 2007-03-09
Thank you so so much for this thread!  I was getting the same errors in CPAN and couldn't figure out why.  I ran conf to check my values and then ran conf commit to make sure they were saved.  Everytime I started CPAN it kept asking me to set these values, it was driving me crazy!  I didn't realize I had to "commit" the values.. :D

A "How To" or at least a CPAN checklist would be great!!

---

### Post by phossal on 2007-03-10
Of course you're welcome ;) I'm sure tr333 would say the same, if he were around.

---

### Post by vinchi007 on 2008-05-04
Thanks for this thread. I had same issue with 7.10 installing XML::RSS

In 'sudo span' had to:
'o conf init' (when you have cpan installed and then add 'sudo apt-get install make', it will not recognize this in perl cpan and you have to run the cpan config again - it should pick it up automatically and if not then specify the path)
'test DateTime::Format::W3CDTF'
'install DateTime::Format::W3CDTF'
'test XML::RSS'
'install XML::RSS'

Make sure that all are successful on make!

---

