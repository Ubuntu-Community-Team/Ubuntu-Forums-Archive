---
title: "anyone else have a broken Swiftweasel after latest upgrade?"
date: 2008-03-28
forum: General Help
---

### Post by Dr.Ninethousand on 2008-03-28
I'm using Kubuntu..

today Adept prompted me to upgrade swiftweasel, and now it won't open..
```

rick@Kutulu:~$ swiftweasel32
/usr/local/bin/swiftweasel32: 7: /usr/local/swiftweasel32/swiftweasel: not found

```

when I look in /usr/local/swiftweasel32/  there is "swiftweasel-bin", but no plain "swiftweasel"..

```

rick@Kutulu:/usr/local/swiftweasel32$ ./swiftweasel-bin
./swiftweasel-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

```

libmozjs.so IS right there in usr/local/swiftweasel32..  I'm looking right at it..


also I should mention I'm running 64bit..  but I never had problems using swiftweasel32 before on this system..

---

### Post by ibuclaw on 2008-03-28
Which repository did you get swiftweasel from?

Regards
Iain

---

### Post by Dr.Ninethousand on 2008-03-28
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) gutsy multiverse


like always..

---

### Post by ibuclaw on 2008-03-28
Appears to be working fine for me.

I just downloaded a deb file (I chose pentium 4 at random, then ran the text script in "/extracted-folder/usr/local/swiftweasel" and it started fine.)

[EDIT]
Moved code to new post
[EDIT]

Regards
Iain

---

### Post by ibuclaw on 2008-03-28
Sorry, I've just had a look round the repo, and found out that you use the amd-gutsy package.

I've have a look, and yes it does seem that the /usr/share/swiftweasel32/swiftweasel script is missing.

And due to the fact that library files may be in a slightly different folder (and architecture) the above script may not work.

None-the-less. I'll have a look at it.
Regards
Iain

---

### Post by Dr.Ninethousand on 2008-03-28
I use swiftweasel32 not swiftweasel..

I do have usr/local/bin/swifweasel32, and it is set to executable..

I do not have usr/local/swiftweasel32/swiftweasel or swiftweasel32..  the only file in there that look similar to yours is called run-mozilla.sh, and it is also marked as executable..


```

rick@Kutulu:/usr/local/swiftweasel32$ ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

```

---

### Post by Dr.Ninethousand on 2008-03-28
> **tinivole said:**
> Sorry, I've just had a look round the repo, and found out that you use the amd-gutsy package.



the package I use is called specifically swiftweasel32-nocona, and is for 32bit support (java, flash) on 64bit Intel, such as my Core2Duo..

thanks for your time  :)

---

### Post by Dr.Ninethousand on 2008-03-28
oh also I've tried using several .deb's from the swiftweasel sourceforge site, but every one of them tells me "wrong architecture 'i386'", whether labeled for AMD or i386..

:confused:

---

### Post by ibuclaw on 2008-03-28
Ok, I've had a look at both the new and old version of the swiftweasel package.

As I said before, the** /usr/share/swiftweasel32/swiftweasel** text file is missing from the deb package, and a fix should be issued or made apparant to the current maintainer.

But for now create a text file with this code in:
```

#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
#
# Software distributed under the License is distributed on an "AS IS" basis,
# WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
# for the specific language governing rights and limitations under the
# License.
#
# The Original Code is mozilla.org Code.
#
# The Initial Developer of the Original Code is
# Netscape Communications Corporation.
# Portions created by the Initial Developer are Copyright (C) 1998
# the Initial Developer. All Rights Reserved.
#
# Contributor(s):
#
# Alternatively, the contents of this file may be used under the terms of
# either the GNU General Public License Version 2 or later (the "GPL"), or
# the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
# in which case the provisions of the GPL or the LGPL are applicable instead
# of those above. If you wish to allow use of your version of this file only
# under the terms of either the GPL or the LGPL, and not to allow others to
# use your version of this file under the terms of the MPL, indicate your
# decision by deleting the provisions above and replace them with the notice
# and other provisions required by the GPL or the LGPL. If you do not delete
# the provisions above, a recipient may use your version of this file under
# the terms of any one of the MPL, the GPL or the LGPL.
#
# ***** END LICENSE BLOCK *****

## $Id: mozilla.in,v 1.12.8.1 2005/09/20 21:13:03 dbaron%dbaron.org Exp $
## 
## Usage:
##
## $ mozilla [args]
##
## This script is meant to run the mozilla-bin binary from either 
## mozilla/xpfe/bootstrap or mozilla/dist/bin.
##
## The script will setup all the environment voodoo needed to make
## the mozilla-bin binary to work.
##

i=~/.mozilla/swiftweasel
if [ -d $i ]
then
echo the settings directory exists 
else
cd ~/.mozilla
cp -r firefox /tmp 
cd /tmp
mv firefox swiftweasel
mv swiftweasel ~/.mozilla/
cd ~/.mozilla/swiftweasel
FILE3="profiles.ini"
OUT3=$(awk -FPath= '{ print $2 }' $FILE3)
mv $OUT3 tmp1
mkdir tmp2
cp -r ./tmp1/extensions ./tmp2
cp -rf ./tmp1/* ./tmp2
mv tmp2 $OUT3
rm -rfd tmp1
fi

cd ~/.mozilla/swiftweasel
FILE4="profiles.ini"
OUT4=$(gawk -FPath= '{ print $2 }' $FILE4)
FILE3="/usr/local/swiftweasel/rpref.txt"
chmod 777 $OUT4/prefs.js
rpref=$(gawk -F=K '{ print $1 }' $FILE3)
echo "$rpref" | tee -ai $OUT4/prefs.js
mv /usr/local/swiftweasel32/swiftweasel /usr/local/swiftweasel32/swiftweasel-ran
mv /usr/local/swiftweasel32/swiftweasel-start /usr/local/swiftweasel32/swiftweasel



moz_pis_startstop_scripts()
{
  MOZ_USER_DIR=".mozilla/swiftweasel"
  # MOZ_PIS_ is the name space for "Mozilla Plugable Init Scripts"
  # These variables and there meaning are specified in
  # mozilla/xpfe/bootstrap/init.d/README
  MOZ_PIS_API=2
  MOZ_PIS_MOZBINDIR="${dist_bin}"
  MOZ_PIS_SESSION_PID="$$"
  MOZ_PIS_USER_DIR="${MOZ_USER_DIR}"
  export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
  
  case "${1}" in
    "start")
      for curr_pis in "${dist_bin}/init.d"/S* "${HOME}/${MOZ_USER_DIR}/init.d"/S* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) .  "${curr_pis}"         ;;
            *)       "${curr_pis}" "start" ;;
          esac
        fi
      done
      ;;
    "stop")
      for curr_pis in "${HOME}/${MOZ_USER_DIR}/init.d"/K* "${dist_bin}/init.d"/K* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) . "${curr_pis}"        ;;
            *)      "${curr_pis}" "stop" ;;
          esac
        fi
      done
      ;;
    *)
      echo 1>&2 "$0: Internal error in moz_pis_startstop_scripts."
      exit 1
      ;;
  esac
}

#uncomment for debugging
#set -x

moz_libdir=/usr/local/swiftweasel32
MRE_HOME=/usr/local/lib/mre/mre-2.0.0.8

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh
found=0
progname="$0"
curdir=`dirname "$progname"`
progbase=`basename "$progname"`
run_moz="$curdir/run-mozilla.sh"
if test -x "$run_moz"; then
  dist_bin="$curdir"
  found=1
else
  here=`/bin/pwd`
  while [ -h "$progname" ]; do
    bn=`basename "$progname"`
    cd `dirname "$progname"`
    progname=`/bin/ls -l "$bn" | sed -e 's/^.* -> //' `
    if [ ! -x "$progname" ]; then
      break
    fi
    curdir=`dirname "$progname"`
    run_moz="$curdir/run-mozilla.sh"
    if [ -x "$run_moz" ]; then
      cd "$curdir"
      dist_bin=`pwd`
      run_moz="$dist_bin/run-mozilla.sh"
      found=1
      break
    fi
  done
  cd "$here"
fi
if [ $found = 0 ]; then
  # Check default compile-time libdir
  if [ -x "$moz_libdir/run-mozilla.sh" ]; then
    dist_bin="$moz_libdir"
  else 
    echo "Cannot find mozilla runtime directory. Exiting."
    exit 1
  fi
fi

script_args=""
debugging=0
MOZILLA_BIN="${progbase}-bin"

if [ "$OSTYPE" = "beos" ]; then
  mimeset -F "$MOZILLA_BIN"
fi

pass_arg_count=0
while [ $# -gt $pass_arg_count ]
do
  case "$1" in
    -p | --pure | -pure)
      MOZILLA_BIN="${MOZILLA_BIN}.pure"
      shift
      ;;
    -g | --debug)
      script_args="$script_args -g"
      debugging=1
      shift
      ;;
    -d | --debugger)
      script_args="$script_args -d $2"
      shift 2
      ;;
    *)
      # Move the unrecognized argument to the end of the list.
      arg="$1"
      shift
      set -- "$@" "$arg"
      pass_arg_count=`expr $pass_arg_count + 1`
      ;;
  esac
done

export MRE_HOME

EXTENT_LD_LIB_PATH=${MOZ_DIST_BIN}:${MOZ_DIST_BIN}/plugins:/usr/lib32/firefox32/plugins
if [ "${LD_LIBRARY_PATH}" ]; then
    LD_LIBRARY_PATH=${EXTENT_LD_LIB_PATH}:${LD_LIBRARY_PATH}
else
    LD_LIBRARY_PATH=${EXTENT_LD_LIB_PATH}
fi
export LD_LIBRARY_PATH

MOZ_PLUGIN_PATH=/usr/lib32/firefox32/plugins${MOZ_PLUGIN_PATH+":$MOZ_PLUGIN_PATH"}
export MOZ_PLUGIN_PATH


## Start addon scripts
moz_pis_startstop_scripts "start"

if [ $debugging = 1 ]
then
  echo $dist_bin/run-mozilla.sh $script_args $dist_bin/$MOZILLA_BIN "$@"
fi
"$dist_bin/run-mozilla.sh" $script_args "$dist_bin/$MOZILLA_BIN" "$@"
exitcode=$?

## Stop addon scripts
moz_pis_startstop_scripts "stop"

exit $exitcode
# EOF.

```

Save it as **swiftweasel**
mark it executable,
and as root, copy it to the swiftweasel folder
```

chmod +x swiftweasel
sudo cp swiftweasel /usr/share/swiftweasel32/

```

That should give you temporary relief for now until the package is upgraded again with a fix for this.
As this is clearly a fault in the package.

Regards
Iain

---

### Post by Dr.Ninethousand on 2008-03-28
:D

hey, perfect!.


I think the Swiftweasel producer can be a little hasty sometimes, in the past I had another problem due to a typo, but I got a quick response and it was an easy fix..



before your last post, I had opened up the Packages.gz and found this info:

Package: swiftweasel-nocona
Essential: no
Priority: optional
Section: web
Maintainer: stickk [getswiftweasel@gmail.com]
Architecture: i386
Version: 2.0.0.13
Filename: pool/i386-gutsy/swiftweasel-2.0.0.13_nocona-**32bit**_ubuntu-i386.deb

(bold added)

and no mention of swiftweasel32-nocona..  so I figured maybe he renamed the packages and forgot to change something somewhere, but after installing that, I had no flash in webpages..

anyway thanks, I'm going to post a link to this at the swiftweasel forums..

---

### Post by Dr.Ninethousand on 2008-03-28
new problem:


after running once, if I close swiftweasel and open it again, the file I added is gone, or renamed to swiftweasel-ran, and I go right back to the previous issues..

---

### Post by Dr.Ninethousand on 2008-03-28
```

rick@Kutulu:~$ swiftweasel32
the settings directory exists
gawk: cmd. line:1: fatal: cannot open file `/usr/local/swiftweasel/rpref.txt' for reading (No such file or directory)

mv: overwrite `/usr/local/swiftweasel32/swiftweasel-ran', overriding mode 0755? 

```


:mad:

---

### Post by ibuclaw on 2008-03-28
hmm...

I've had another look, and have decided to run it in a sandbox.

This was printed in a the terminal:

```

mv: cannot stat `/usr/local/swiftweasel32/swiftweasel': No such file or directory
mv: cannot stat `/usr/local/swiftweasel32/swiftweasel-start': No such file or directory

```

So I had a skim through the swiftweasel text file to find this
```

mv /usr/local/swiftweasel32/swiftweasel /usr/local/swiftweasel32/swiftweasel-ran
mv /usr/local/swiftweasel32/swiftweasel-start /usr/local/swiftweasel32/swiftweasel

```

I manually made the change, and it seemed to start all good!

Okay, here's a fix: :)

First, rename the changed file back to its original name.
```

sudo mv /usr/local/swiftweasel32/swiftweasel-ran /usr/local/swiftweasel32/swiftweasel

```

And then, open up a new text file, and paste this in
```

#!/bin/sh
#
# ***** BEGIN LICENSE BLOCK *****
# Version: MPL 1.1/GPL 2.0/LGPL 2.1
#
# The contents of this file are subject to the Mozilla Public License Version
# 1.1 (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
# http://www.mozilla.org/MPL/
#
# Software distributed under the License is distributed on an "AS IS" basis,
# WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
# for the specific language governing rights and limitations under the
# License.
#
# The Original Code is mozilla.org Code.
#
# The Initial Developer of the Original Code is
# Netscape Communications Corporation.
# Portions created by the Initial Developer are Copyright (C) 1998
# the Initial Developer. All Rights Reserved.
#
# Contributor(s):
#
# Alternatively, the contents of this file may be used under the terms of
# either the GNU General Public License Version 2 or later (the "GPL"), or
# the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
# in which case the provisions of the GPL or the LGPL are applicable instead
# of those above. If you wish to allow use of your version of this file only
# under the terms of either the GPL or the LGPL, and not to allow others to
# use your version of this file under the terms of the MPL, indicate your
# decision by deleting the provisions above and replace them with the notice
# and other provisions required by the GPL or the LGPL. If you do not delete
# the provisions above, a recipient may use your version of this file under
# the terms of any one of the MPL, the GPL or the LGPL.
#
# ***** END LICENSE BLOCK *****

## $Id: mozilla.in,v 1.12.8.1 2005/09/20 21:13:03 dbaron%dbaron.org Exp $
## 
## Usage:
##
## $ mozilla [args]
##
## This script is meant to run the mozilla-bin binary from either 
## mozilla/xpfe/bootstrap or mozilla/dist/bin.
##
## The script will setup all the environment voodoo needed to make
## the mozilla-bin binary to work.
##

i=~/.mozilla/swiftweasel
if [ -d $i ]
then
echo the settings directory exists 
else
cd ~/.mozilla
cp -r firefox /tmp 
cd /tmp
mv firefox swiftweasel
mv swiftweasel ~/.mozilla/
cd ~/.mozilla/swiftweasel
FILE3="profiles.ini"
OUT3=$(awk -FPath= '{ print $2 }' $FILE3)
mv $OUT3 tmp1
mkdir tmp2
cp -r ./tmp1/extensions ./tmp2
cp -rf ./tmp1/* ./tmp2
mv tmp2 $OUT3
rm -rfd tmp1
fi


moz_pis_startstop_scripts()
{
  MOZ_USER_DIR=".mozilla/swiftweasel"
  # MOZ_PIS_ is the name space for "Mozilla Plugable Init Scripts"
  # These variables and there meaning are specified in
  # mozilla/xpfe/bootstrap/init.d/README
  MOZ_PIS_API=2
  MOZ_PIS_MOZBINDIR="${dist_bin}"
  MOZ_PIS_SESSION_PID="$$"
  MOZ_PIS_USER_DIR="${MOZ_USER_DIR}"
  export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
  
  case "${1}" in
    "start")
      for curr_pis in "${dist_bin}/init.d"/S* "${HOME}/${MOZ_USER_DIR}/init.d"/S* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) .  "${curr_pis}"         ;;
            *)       "${curr_pis}" "start" ;;
          esac
        fi
      done
      ;;
    "stop")
      for curr_pis in "${HOME}/${MOZ_USER_DIR}/init.d"/K* "${dist_bin}/init.d"/K* ; do
        if [ -x "${curr_pis}" ] ; then
          case "${curr_pis}" in
            *.sh) . "${curr_pis}"        ;;
            *)      "${curr_pis}" "stop" ;;
          esac
        fi
      done
      ;;
    *)
      echo 1>&2 "$0: Internal error in moz_pis_startstop_scripts."
      exit 1
      ;;
  esac
}

#uncomment for debugging
#set -x

moz_libdir=/usr/local/swiftweasel32
MRE_HOME=/usr/local/lib/mre/mre-2.0.0.8

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh
found=0
progname="$0"
curdir=`dirname "$progname"`
progbase=`basename "$progname"`
run_moz="$curdir/run-mozilla.sh"
if test -x "$run_moz"; then
  dist_bin="$curdir"
  found=1
else
  here=`/bin/pwd`
  while [ -h "$progname" ]; do
    bn=`basename "$progname"`
    cd `dirname "$progname"`
    progname=`/bin/ls -l "$bn" | sed -e 's/^.* -> //' `
    if [ ! -x "$progname" ]; then
      break
    fi
    curdir=`dirname "$progname"`
    run_moz="$curdir/run-mozilla.sh"
    if [ -x "$run_moz" ]; then
      cd "$curdir"
      dist_bin=`pwd`
      run_moz="$dist_bin/run-mozilla.sh"
      found=1
      break
    fi
  done
  cd "$here"
fi
if [ $found = 0 ]; then
  # Check default compile-time libdir
  if [ -x "$moz_libdir/run-mozilla.sh" ]; then
    dist_bin="$moz_libdir"
  else 
    echo "Cannot find mozilla runtime directory. Exiting."
    exit 1
  fi
fi

script_args=""
debugging=0
MOZILLA_BIN="${progbase}-bin"

if [ "$OSTYPE" = "beos" ]; then
  mimeset -F "$MOZILLA_BIN"
fi

pass_arg_count=0
while [ $# -gt $pass_arg_count ]
do
  case "$1" in
    -p | --pure | -pure)
      MOZILLA_BIN="${MOZILLA_BIN}.pure"
      shift
      ;;
    -g | --debug)
      script_args="$script_args -g"
      debugging=1
      shift
      ;;
    -d | --debugger)
      script_args="$script_args -d $2"
      shift 2
      ;;
    *)
      # Move the unrecognized argument to the end of the list.
      arg="$1"
      shift
      set -- "$@" "$arg"
      pass_arg_count=`expr $pass_arg_count + 1`
      ;;
  esac
done

export MRE_HOME

EXTENT_LD_LIB_PATH=${MOZ_DIST_BIN}:${MOZ_DIST_BIN}/plugins:/usr/lib32/firefox32/plugins
if [ "${LD_LIBRARY_PATH}" ]; then
    LD_LIBRARY_PATH=${EXTENT_LD_LIB_PATH}:${LD_LIBRARY_PATH}
else
    LD_LIBRARY_PATH=${EXTENT_LD_LIB_PATH}
fi
export LD_LIBRARY_PATH

MOZ_PLUGIN_PATH=/usr/lib32/firefox32/plugins${MOZ_PLUGIN_PATH+":$MOZ_PLUGIN_PATH"}
export MOZ_PLUGIN_PATH


## Start addon scripts
moz_pis_startstop_scripts "start"

if [ $debugging = 1 ]
then
  echo $dist_bin/run-mozilla.sh $script_args $dist_bin/$MOZILLA_BIN "$@"
fi
"$dist_bin/run-mozilla.sh" $script_args "$dist_bin/$MOZILLA_BIN" "$@"
exitcode=$?

## Stop addon scripts
moz_pis_startstop_scripts "stop"

exit $exitcode
# EOF.

```

Then its the same steps as my previous post.
(Save as "**swiftweasel-start**", "**chmod +x swiftweasel-start**" and "**sudo cp swiftweasel-start /usr/local/swiftweasel32/**

Then run the swiftweasel as normal, then the correct file changes should be applied.

Hope this solves it.
Though I can't guarentee anything. But that's why I'm here to help if you find yourself in another hole. 

Regards

---

### Post by Dr.Ninethousand on 2008-03-28
ha, I had to do all of these steps a couple of times in various orders, as it kept removing the swiftweasel text..

but, I've closed and re-opened Swiftweasel32 a few times now and it seems to be working finally.. 


:)

---

