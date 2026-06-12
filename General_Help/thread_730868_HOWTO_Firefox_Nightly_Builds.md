---
title: "HOWTO: Firefox Nightly Builds"
date: 2008-03-21
forum: General Help
---

### Post by Craga_89 on 2008-03-21
[SIZE="6"]HOWTO: Firefox Nightly Builds[/SIZE]

Recently I've been testing out the latest Firefox nightly builds and updating them can become a real pain if your not sure what your doing. I've made a quick bash script to check if a new version is available and install it.

[SIZE="5"]Info:[/SIZE]
The default installation directory for the new nightly build is:
```
/usr/lib/firefox-nightly
```
New firefox nightly builds are downloaded from:
```
http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/
```
The script **automatically creates a symbolic link to your proper firefox plugins** folder so you can enjoy all your old plugins in the new build.

[SIZE="5"]Instructions[/SIZE]
**[SIZE="4"]Step 1:[/SIZE]**
Extract the script into your local binary directory:
```
tar -C /usr/local/bin -xvzf firefox-nightly.tar.gz
```

**[SIZE="4"]Step 2:[/SIZE]**
Ensure the file is executable by running this command:
```
chmod +x /usr/local/bin/firefox-nightly
```

**[SIZE="4"]Step 3:[/SIZE]**
Run the command via terminal:
```
firefox-nightly
```


[SIZE="5"]Script contents:[/SIZE]
```

#!/bin/bash

# ========================================================
# Configuration
# ========================================================

# URL to build page
url="http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/"

# System path to install nightly build
installdir="/usr/lib/firefox-nightly"

# Temporary index.html file path
tmp="/tmp/index.html"

# ========================================================
# End configuration
# ========================================================

# Change to temp directory
cd /tmp

# Download index and find nightly builds name
wget -q -c -O "$tmp" "$url"
name=$(sed -n 's/.*<a href="\(.*.tar.bz2\)">.*/\1/ip;T;q' "$tmp")
rm "$tmp"

# Retrieve current nightly version
if [ -f "$installdir/application.ini" ]; then
   version=$(sed -n 's/.*Version=\(.+\)*/\1/ip;T;q' "$installdir/application.ini")
else
   version="00.00.00"
fi

# Is version already installed?
installed=$(echo "$name" | egrep -c "$version")
if [ $installed = "1" ]; then
   echo "Firefox nightly is already up to date. Exiting..."
else
   # Download new nightly build and extract
   wget -c -O "/tmp/$name" "$url$name"
   tar xvjf "$name"
   
   # Delete old build files and move new
   sudo rm -r "$installdir"
   sudo mv ./firefox "$installdir"
   
   # Create plugins symlink
   ln -s "/usr/lib/firefox/plugins" "$installdir/plugins"

   # Echo success
   newver=$(sed -n 's/.*Version=\(.+\)*/\1/ip;T;q' "$installdir/application.ini")
   echo "Firefox nightly successfully updated! (Ver: $newver)"
fi

```

[COLOR="Red"][SIZE="5"]WARNING:[/SIZE][/COLOR]
The script removes all files in the install directory during install of the new build! I won't take responsibility for this script messing up your current Firefox installation.

Have fun!

---

### Post by kindofabuzz on 2008-05-05
Yes the script works, but for the nightly.  it gets the most recent trunk, but if you do it daily it still says there is no newer version.

---

### Post by alex_mayorga on 2008-05-08
Any chance Firefox Nightly Builds could be put in somebody's PPA?

So far I've been using Fabien Tassin's at [https://edge.launchpad.net/~fta/+archive](https://edge.launchpad.net/~fta/+archive) but I'm really not sure if it contains Nightly Builds.

Thanks in advance,
Alex

---

