---
title: "Chromium vs. Chromium - Snapping Intensifies"
date: 2021-06-24
forum: General Help
---

### Post by Shibblet on 2021-06-24
Alright... got a problem here.

I am trying to download this particular version of Chromium, available with a PPA.  However, when I add this PPA, APT doesn't seem to care, and installs the current Snap Package anyway.

[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta]("https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta")

How can I stop APT from ignoring this PPA and choosing the Snap package instead?

I've actually even attempted to remove "Snap" itself, and then tried downloading the Chromium Package.  I sat there in complete disbelief as I watched APT install Snap, and then Snap install Chromium... almost like a giant middle-finger to my face.

---

### Post by monkeybrain20122 on 2021-06-24
I think snap and apt are separate, no?

I don't use chromium but just add the ppa for a test

```
$apt -s install chromium-browser
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  chromium-browser-l10n chromium-codecs-ffmpeg-extra libpipewire-0.2-1
Suggested packages:
  webaccounts-chromium-extension unity-chromium-extension chromiumflashplugin
The following NEW packages will be installed:
  chromium-browser chromium-browser-l10n libpipewire-0.2-1
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra
1 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
Inst libpipewire-0.2-1 (0.2.7-1 Ubuntu:20.04/focal [amd64])
Inst chromium-codecs-ffmpeg-extra [1:85.0.4183.83-0ubuntu0.20.04.2] (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [amd64])
Inst chromium-browser (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [amd64])
Inst chromium-browser-l10n (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [all])
Conf libpipewire-0.2-1 (0.2.7-1 Ubuntu:20.04/focal [amd64])
Conf chromium-codecs-ffmpeg-extra (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [amd64])
Conf chromium-browser (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [amd64])
Conf chromium-browser-l10n (1:91.0.4472.27-0ubuntu1~ppa3~20.04.1 Chromium Beta branch:20.04/focal [all])
```

Doesn't seem to install any snap stuff.

BTW my system is snap free, got rid of and purged all snap things in the beginning so if there is any snap related package as dependencies it would have to be reinstalled, none  on the list above.

Which Ubuntu version are you using?

---

### Post by Shibblet on 2021-06-24
> **monkeybrain20122 said:**
> Doesn't seem to install any snap stuff.

BTW my system is snap free, got rid of and purged all snap things in the beginning so if there is any snap related package as dependencies it would have to be reinstalled, none  on the list above.

Which Ubuntu version are you using?

I am currently running 21.04.

Chromium as a "Snap" has been implemented since 20.10.

---

### Post by tea for one on 2021-06-24
Apt will install a script, which then installs the snap version of chromium-browser.

```
edited@edited:~$ apt show -a chromium-browser
Package: chromium-browser
Version: 1:85.0.4183.83-0ubuntu0.20.04.2
Priority: optional
Section: universe/web
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 164 kB [COLOR="#0000FF"]too small for a browser[/COLOR]
Provides: gnome-www-browser, www-browser, x-www-browser
Pre-Depends: debconf, snapd
Depends: debconf (>= 0.5) | debconf-2.0
Homepage: https://chromium.googlesource.com/chromium/src/
Download-Size: 48.3 kB
APT-Sources: http://gb.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
Description: Transitional package - chromium-browser -> chromium snap
 This is a transitional dummy package. It can safely be removed.
 .
 chromium-browser is now replaced by the [COLOR="#0000FF"]chromium snap[/COLOR].

```
> **Shibblet said:**
> How can I stop APT from ignoring this PPA and choosing the Snap package instead?

Can you uncheck all your software sources and leave the PPA active as a source?
Then, you should only receive the desired PPA package.

Don't forget to re-activate your sources afterwards.

---

### Post by monkeybrain20122 on 2021-06-24
> **tea for one said:**
> Apt will install a script, which then installs the snap version of chromium-browser.


  ```
...
Package: chromium-browser
Version: **1:85.0**.4183.83-0ubuntu0.20.04.2
...


```

Can you uncheck all your software sources and leave the PPA active as a source?
Then, you should only receive the desired PPA package.

Don't forget to re-activate your sources afterwards.

But that is the chroumium-browser in the standard repo, not from the ppa, the  ppa version is **1:91.0**, in the official repo it is **1:85.0**


from synaptic, chromium-browser in the official repo is described as 

> Transitional package - chromium-browser -> chromium snap

 But there is no mention of snap for chromium-browser with the ppa. You can also go to the ppa's page and click "view package details" for Ubuntu 21.04 (OP's Ubuntu's version)
They are all standard .debs, no snap script or anything, sure doesn't look like a transitional package to install chormium from snap.



now without the ppa (official repo)

```
$apt -s install chromium-browser
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  **snapd**
The following NEW packages will be installed:
  **chromium-browser snapd**
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst snapd (2.49.2+20.04 Ubuntu:20.04/focal-updates [amd64])
Conf snapd (2.49.2+20.04 Ubuntu:20.04/focal-updates [amd64])
Inst chromium-browser (1:85.0.4183.83-0ubuntu0.20.04.2 Ubuntu:20.04/focal-updates [amd64])
Conf chromium-browser (1:85.0.4183.83-0ubuntu0.20.04.2 Ubuntu:20.04/focal-updates [amd64])

```

This is different from the output above when  the ppa was activated.

---

### Post by Shibblet on 2021-06-24
> **tea for one said:**
> Apt will install a script, which then installs the snap version of chromium-browser.
Yep.  That's the issue.

> **tea for one said:**
> Can you uncheck all your software sources and leave the PPA active as a source?
Then, you should only receive the desired PPA package.

Don't forget to re-activate your sources afterwards.

I have tried that as well.  No matter what I do, I cannot use this PPA.  The script that APT installs apparently cuts in line in front of the PPA.

It's like the PPA I want to use is the crew of the Enterprise, and the APT script is William Shatner.

---

### Post by monkeybrain20122 on 2021-06-24
Well after you add the ppa, you can check the version. It could be that the packages for your Ubuntu version failed to build or something so it reverts to the official repo's. 

If everything fails, you can download the .debs from the ppa and install them manually. Click "view package details" on the ppa's page, choose the version for Ubuntu 21.04 and download all the debs you need for your architecture. Put them in one folder say, chromuim, then

```
cd chromium

sudo dpkg -i *
```

P.S There is also a chromium for flatpak callled ungoogled-chromium. You may try that also, it seems that flatpak is a somewhat cleaner way to install apps than snap, it allows easier access control through flatseal and doesn't mount a whole bunch of volumes.

---

### Post by Shibblet on 2021-06-24
> **monkeybrain20122 said:**
> Well after you add the ppa, you can check the version. It could be that the packages for your Ubuntu version failed to build or something so it reverts to the official repo's. 

If everything fails, you can download the .debs from the ppa and install them manually. Click "view package details" on the ppa's page, choose the version for Ubuntu 21.04 and download all the debs you need for your architecture. Put them in one folder say, chromuim, then

```
cd chromium

sudo dpkg -i *
```

That unfortunately doesn't work.  When using APT in Bash, you can actually watch (in horror) as it installs the Snap instead of your PPA.

> **monkeybrain20122 said:**
> P.S There is also a chromium for flatpak callled ungoogled-chromium. You may try that also, it seems that flatpak is a somewhat cleaner way to install apps than snap, it allows easier access control through flatseal and doesn't mount a whole bunch of volumes.

Much appreciated.  However, the PPA in question is a specific build of Chromium, for my needs.

---

### Post by monkeybrain20122 on 2021-06-24
You got me curious so I downloaded the .deb (Chromium-browser) from the ppa for Ubuntu21.04, extract it and checked the contents. 

The bin file looks like this
```
#!/bin/bash

# Chromium launcher

# Authors:
#  Chad Miller <chad.miller@canonical.com>
#  Fabien Tassin <fta@sofaraway.org>
# License: GPLv2 or later

PLUGIN_PARAMETERS=""

discover_registration () {
    local FILE_NAME
    local PLUGIN_NAME
    local VERSION
    local VISIBLE_VERSION
    local DESCRIPTION
    local MIME_TYPES

    registration_file=$1
    option_prefix=$2

    test -f "${registration_file}" || return 1
    . "${registration_file}" 

    test "$VERSION" || return 2
    test "$FILE_NAME" || return 3

    echo "$PLUGIN_PARAMETERS" |grep -- "--${option_prefix}-path=" >/dev/null && return 4

    PLUGIN_PARAMETERS="--${option_prefix}-path=${FILE_NAME} --${option_prefix}-version=${VERSION%%-*} ${PLUGIN_PARAMETERS}"
    return 0
}

# Explicitly set the PATH to that of ENV_SUPATH in /etc/login.defs and unset
# various other variables. (LP: #1045986). This can be removed once AppArmor
# supports environment filtering (LP: #1045985)
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
export ENV=
export BASH_ENV=
export CDPATH=
export GLOBIGNORE=
export BASH_XTRACEFD=

if grep -E -w ^Features\\s\*:.\*neon /proc/cpuinfo >/dev/null; then
    export CPU_FEATURE_NEON=1
fi
if grep -E -w ^flags\\s\*:.\*sse /proc/cpuinfo >/dev/null; then
    export CPU_FEATURE_SSE=1
fi
export CPU_FEATURES_TESTED=1

readonly APPNAME=chromium-browser
LIBDIR=/usr/lib/chromium-browser
GDB=/usr/bin/gdb
readonly BUILD_DIST="Ubuntu 21.04"
readonly UPSTREAM_VERSION="1:91.0.4472.27"
if test -x "${LIBDIR}/${UPSTREAM_VERSION}"/chromium-browser; then
    LIBDIR="${LIBDIR}/${UPSTREAM_VERSION}"
fi
readonly LIBDIR

usage () {
  echo "$APPNAME [-h|--help] [-g|--debug] [--temp-profile] [--no-touch-pinch] [options] [URL]"
  echo
  echo "        --verbose               Events logged to stderr."
  echo "        -g or --debug           Start within $GDB"
  echo "        -h or --help            This help screen"
  echo "        --temp-profile          Start with a new and temporary profile"
  echo "        --no-touch-pinch        Disable pinch gestures."
  echo
  echo " Other supported options are:"
  MANWIDTH=80 man chromium-browser | sed -e '1,/OPTIONS/d; /ENVIRONMENT/,$d'
  echo " See 'man chromium-browser' for more details"
}

if [ -f /etc/$APPNAME/default ] ; then
  . /etc/$APPNAME/default
fi

if test -d /etc/$APPNAME/customizations; then
    while read f; do
        . "$f"
    done < <(run-parts --list -- /etc/$APPNAME/customizations)
fi
test -f ~/.chromium-browser.init && . ~/.chromium-browser.init

FLASH_GOOD_PACKAGE="adobe-flashplugin"
if test "$FLASH_GOOD_PACKAGE"; then
    PREVIOUS_CANDIDATE=""
    CANDIDATE="$CHROMIUM_FLAGS"
    while test "$PREVIOUS_CANDIDATE" != "$CANDIDATE"; do  # Strip ppapi-flash-xxxx params off that are outside our known good params, for as long as we still make progress.
        PREVIOUS_CANDIDATE="$CANDIDATE"
        CANDIDATE=$(echo "$CANDIDATE" |sed -e "s,--ppapi-flash-\w*=\S*\s\(.*--ppapi-flash-path=/usr/lib/${FLASH_GOOD_PACKAGE}/libpepflashplayer.so --ppapi-flash-version=\),\1,")
        CANDIDATE=$(echo "$CANDIDATE" |sed -e "s,\(.*--ppapi-flash-path=/usr/lib/${FLASH_GOOD_PACKAGE}/libpepflashplayer.so --ppapi-flash-version=.*\) --ppapi-flash-\w*=\S*,\1,")
    done
    CHROMIUM_FLAGS="$CANDIDATE"
fi

if test -x /usr/bin/python3 -a -f "/usr/lib/adobe-flashplugin/manifest.json"; then
    if echo "$CHROMIUM_FLAGS" |grep -E -- "--ppapi-flash-version=( |\$)"; then
        ver=$(python -c 'import json,sys; print(json.load(open("/usr/lib/adobe-flashplugin/manifest.json"))["version"]);')
        CHROMIUM_FLAGS=${CHROMIUM_FLAGS/--ppapi-flash-version=/--ppapi-flash-version="${ver}" }
    fi
fi

# Prefer user defined CHROMIUM_USER_FLAGS (fron env) over system
# default CHROMIUM_FLAGS (from /etc/$APPNAME/default)
if test -n "$CHROMIUM_USER_FLAGS"; then
    echo "WARNING: \$CHROMIUM_USER_FLAGS is deprecated. Instead, update CHROMIUM_FLAGS in ~/.chromium-browser.init or place configuration for all users in /etc/$APPNAME/customizations/ ."
    echo "WARNING: Ignoring system flags because \$CHROMIUM_USER_FLAGS is set."
    echo "CHROMIUM_FLAGS=${CHROMIUM_FLAGS}"
    echo "CHROMIUM_USER_FLAGS=${CHROMIUM_USER_FLAGS}"
    CHROMIUM_FLAGS=${CHROMIUM_USER_FLAGS}
fi

# For the Default Browser detection to work, we need to give access
# to xdg-settings if it's not present on the system (ensures that the system
# xdg-utils is recent enough). Also set CHROME_WRAPPER in case xdg-settings is
# not able to do anything useful
if [ ! -e /usr/bin/xdg-settings ] ; then
  export PATH="$LIBDIR:$PATH"
fi
export CHROME_WRAPPER="`readlink -f "$0"`"
export CHROME_DESKTOP=$APPNAME.desktop

# lsb_release is slow so try to source the static file /etc/lsb-release instead
if [ -e /etc/lsb-release ] ; then
  . /etc/lsb-release
fi
# Fall back to lsb_release if we didn't get the information we need
if test -z "${DISTRIB_ID:-}"; then
    DIST=$(lsb_release -si)
    RELEASE=$(lsb_release -sr)
else
    DIST=${DISTRIB_ID}
    RELEASE=${DISTRIB_RELEASE}
fi

# Set CHROME_VERSION_EXTRA visible in the About dialog and in about:version
if [ "$DIST $RELEASE" = "$BUILD_DIST" ] ; then
  export CHROME_VERSION_EXTRA="$DIST $RELEASE"
else
  export CHROME_VERSION_EXTRA="Built on $BUILD_DIST, running on $DIST $RELEASE"
fi

want_touch_pinch=1
want_debug=0
want_temp_profile=0
want_verbose=0
while [ $# -gt 0 ]; do
  case "$1" in
    -h | --help | -help )
      usage
      exit 0 ;;
    --verbose )
      want_verbose=1
      shift ;;
    -g | --debug )
      want_debug=1
      shift ;;
    --no-touch-pinch )
      want_touch_pinch=0
      shift ;;
    --temp-profile )
      want_temp_profile=1
      shift ;;
    -- ) # Stop option prcessing
      shift
      break ;;
    * )
      break ;;
  esac
done

discover_registration ${LIBDIR}/pepper/pepper-flash.info ppapi-flash && echo "Pepper Flash detected."

CHROMIUM_FLAGS="${CHROMIUM_FLAGS} ${PLUGIN_PARAMETERS}"

if [ $want_verbose -eq 1 ] ; then
  CHROMIUM_FLAGS="${CHROMIUM_FLAGS} --enable-logging=stderr --v=${want_verbose}"
fi

if [ $want_temp_profile -eq 1 ] ; then
  TEMP_PROFILE=`mktemp -d`
  CHROMIUM_FLAGS="$CHROMIUM_FLAGS --user-data-dir=$TEMP_PROFILE"
fi

if [ $want_touch_pinch -eq 1 ] ; then
  CHROMIUM_FLAGS="$CHROMIUM_FLAGS --enable-pinch"
fi

if [ $want_debug -eq 1 ] ; then
  if [ ! -x $GDB ] ; then
    echo "Sorry, can't find usable $GDB. Please install it."
    exit 1
  fi
  tmpfile=`mktemp /tmp/chromiumargs.XXXXXX` || { echo "Cannot create temporary file" >&2; exit 1; }
  trap " [ -f \"$tmpfile\" ] && /bin/rm -f -- \"$tmpfile\"" 0 1 2 3 13 15
  echo "set args $CHROMIUM_FLAGS ${1+"$@"}" > $tmpfile
  echo "# Env:"
  echo "#     LD_LIBRARY_PATH=$LD_LIBRARY_PATH"
  echo "#                PATH=$PATH"
  echo "#            GTK_PATH=$GTK_PATH"
  echo "# CHROMIUM_USER_FLAGS=$CHROMIUM_USER_FLAGS"
  echo "#      CHROMIUM_FLAGS=$CHROMIUM_FLAGS"
  echo "$GDB $LIBDIR/$APPNAME -x $tmpfile"
  $GDB "$LIBDIR/$APPNAME" -x $tmpfile
  if [ $want_temp_profile -eq 1 ] ; then
    rm -rf $TEMP_PROFILE
  fi
  exit $?
else
  if [ $want_temp_profile -eq 0 ] ; then
    exec $LIBDIR/$APPNAME $CHROMIUM_FLAGS "$@"
  else
    # we can't exec here as we need to clean-up the temporary profile
    $LIBDIR/$APPNAME $CHROMIUM_FLAGS "$@"
    rm -rf $TEMP_PROFILE
  fi
fi


```

So you see it loads things from directories like /usr/bin, /usr/lib etc, this is normal places where application components go to. It doesn't run Chromium from snap.

Now go to [https://launchpad.net/ubuntu/+source/chromium-browser](https://launchpad.net/ubuntu/+source/chromium-browser) to  download the deb in the official repo (note that Ubuntu 18.04 has  version 91 same as ppa but Ubuntu 29.04 on has 85 (snap)


the bin file , see the last line.


```
#!/bin/sh
if ! [ -x /snap/bin/chromium ]; then
    echo "" >&2
    echo "Command '$0' requires the chromium snap to be installed." >&2
    echo "Please install it with:" >&2
    echo "" >&2
    echo "snap install chromium" >&2
    echo "" >&2
    exit 1
fi

if [ "$(xdg-settings get default-web-browser)" = "chromium-browser.desktop" ]; then
  xdg-settings set default-web-browser chromium_chromium.desktop
fi

# GNOME Shell
OLD="chromium-browser.desktop"
NEW="chromium_chromium.desktop"
FAVS=$(gsettings get org.gnome.shell favorite-apps 2> /dev/null)
if echo "$FAVS" | grep -q "'$OLD'"; then
  NEWFAVS=$(echo $FAVS | sed -e "s#'$OLD'#'$NEW'#")
  gsettings set org.gnome.shell favorite-apps "$NEWFAVS"
fi

# Unity
OLD="application://chromium-browser.desktop"
NEW="application://chromium_chromium.desktop"
FAVS=$(gsettings get com.canonical.Unity.Launcher favorites 2> /dev/null)
if echo "$FAVS" | grep -q "'$OLD'"; then
  NEWFAVS=$(echo $FAVS | sed -e "s#'$OLD'#'$NEW'#")
  gsettings set com.canonical.Unity.Launcher favorites "$NEWFAVS"
fi

# MATE
OLD="/usr/share/applications/chromium-browser.desktop"
NEW="/var/lib/snapd/desktop/applications/chromium_chromium.desktop"
OBJECTS=$(gsettings get org.mate.panel object-id-list 2> /dev/null)
for object in $OBJECTS; do
  object=$(echo $object | cut -d\' -f2)
  launcher=$(gsettings get org.mate.panel.object:/org/mate/panel/objects/$object/ launcher-location)
  if [ "$launcher" = "'$OLD'" ]; then
    gsettings set org.mate.panel.object:/org/mate/panel/objects/$object/ launcher-location "'$NEW'"
  fi
done

# KDE Plasma
if which qdbus > /dev/null; then
  SCRIPT="$(cat <<-EOF
    for (var i = 0; i < panelIds.length; ++i) {
      var panel = panelById(panelIds[i]);
      var widgets = panel.widgets();
      for (var j = 0; j < widgets.length; ++j) {
        var widget = widgets[j];
        if (widget.type == "org.kde.plasma.taskmanager") {
          widget.currentConfigGroup = "General";
          var launchers = widget.readConfig("launchers");
          if (launchers.includes("chromium-browser.desktop")) {
            widget.writeConfig("launchers", launchers.replace(/chromium-browser.desktop/g, "chromium_chromium.desktop"));
          }
        }
      }
    }
EOF
  )"
  qdbus org.kde.plasmashell /PlasmaShell org.kde.PlasmaShell.evaluateScript "$SCRIPT" 2> /dev/null
fi

# TODO: handle other desktop environments

**exec /snap/bin/chromium** "$@"

```


So the ppa version is not a script to pull in the snap and apt shouldn't be installing the official repo's version if the ppa is properly activated. Did you check the version when the ppa is activated?

If you downloaded the debs maybe try dpkg instead of apt, apt may be too smart and do things like versoning you may not want in this instance.

---

### Post by monkeybrain20122 on 2021-06-24
You can also purge snap and put an apt-hold on snapd so it won't be reinstall as a dependencies. Then install chromium from ppa and see how it goes. Though it is really weird since the ppa has a higher version and should override the repo's.

---

### Post by coffeecat on 2021-06-25
> **Shibblet said:**
> 
How can I stop APT from ignoring this PPA and choosing the Snap package instead?


I've not tried this for myself, but did [Catkiller's suggestion about changing pin priority](https://ubuntuforums.org/showthread.php?t=2461281&p=14035004&viewfull=1#post14035004) from your earlier [earlier thread about the same issue](https://ubuntuforums.org/showthread.php?t=2461281) help?

---

### Post by tea for one on 2021-06-25
> **Shibblet said:**
> No matter what I do, I cannot use this PPA.  The script that APT installs apparently cuts in line in front of the PPA.

It's like the PPA I want to use is the crew of the Enterprise, and the APT script is William Shatner.

I have no idea where apt installs this script but you should be able to find it and delete it?
Then, try again by unchecking all sources except the PPA.

Any luck?

---

### Post by monkeybrain20122 on 2021-06-25
I think may be the ppa version is not installable in your system because some dependencies cannot be met, in that case apt would install the version that would meet the requirement, i.e 85 from official repo which is a script to install snap. This can be caused either by packaging issues with the ppa or you have pinned some packages or added some ppa that boosted some dependencies to a higher version and then delete the ppa so your versions of these packages are out of sync with your software sources. To locate the problem you can try to install the deb you downloaded (either in the directory that contains the deb do sudo apt install ./debpackage instead of just sudo apt install debpackage, or use gdebi) and see the error messages.

---

### Post by ajgreeny on 2021-06-25
Have a look in synaptic which you may have to install, but you will see in that from the Origin option in the left hand pane what is actually available from the various repos.

Check that the PPA really is enabled and the version offered in that, then still using synaptic, see what happens if you try to install the PPA version from there.

---

### Post by Shibblet on 2021-06-25
> **monkeybrain20122 said:**
> You can also purge snap and put an apt-hold on snapd so it won't be reinstall as a dependencies. Then install chromium from ppa and see how it goes. Though it is really weird since the ppa has a higher version and should override the repo's.

Like I said in my initial post.  I have tried that.  It does not override anything.  APT reinstalls Snap, and then Snap installs Chromium.

> **monkeybrain20122 said:**
> I think may be the ppa version is not installable in your system because some dependencies cannot be met, in that case apt would install the version that would meet the requirement, i.e 85 from official repo which is a script to install snap. This can be caused either by packaging issues with the ppa or you have pinned some packages or added some ppa that boosted some dependencies to a higher version and then delete the ppa so your versions of these packages are out of sync with your software sources. To locate the problem you can try to install the deb you downloaded (either in the directory that contains the deb do sudo apt install ./debpackage instead of just sudo apt install debpackage, or use gdebi) and see the error messages.

That's a good possibility.  I looked, and don't have any packages "pinned" in Muon.  So, I'm not sure how to check out these dependencies before hand...  

This is really just strange.  I have never had any issues with PPA's in the past.  And it seems as if Chromium is the only one that does.

---

### Post by Shibblet on 2021-06-25
> **coffeecat said:**
> I've not tried this for myself, but did [Catkiller's suggestion about changing pin priority](https://ubuntuforums.org/showthread.php?t=2461281&p=14035004&viewfull=1#post14035004) from your earlier [earlier thread about the same issue](https://ubuntuforums.org/showthread.php?t=2461281) help?

Yeah, I tried that too.  No workie.

---

### Post by monkeybrain20122 on 2021-06-25
> **Shibblet said:**
> Like I said in my initial post.  I have tried that.  It does not override anything.  APT reinstalls Snap, and then Snap installs Chromium.



That's a good possibility.  I looked, and don't have any packages "pinned" in Muon.  So, I'm not sure how to check out these dependencies before hand...  

This is really just strange.  I have never had any issues with PPA's in the past.  And it seems as if Chromium is the only one that does.


Have you try disabling all sources but the ppa and install like tea suggested? 

Also you can figure out if there are missing or unmet dependencies if you just grab the .deb from the ppa and do (cd into the directory where the .deb is)
```
sudo apt install ./chromium-browserxxx.deb
```

Don't forget the ./ as you try to install that particular deb that you download. 

Post the outputs if it still installs 85 from main repository.

---

### Post by Paddy Landau on 2021-11-17
I've just tried this with Lubuntu 21.04 in a VM, and I see what you mean!

This must be Canonical's way of avoiding having to go through the process of updating its PPA all the time, which it would otherwise have to do for security reasons.

I did two things.

**One: Flatpak**

I installed Chromium using Flatpak. This worked perfectly.
```
$ flatpak list --app
Name                         Application ID                Version              Branch        Installation
Chromium Web Browser         org.chromium.Chromium         96.0.4664.45         stable        system
```
Unfortunately, this isn't the beta version that you want. As far as I can tell, the beta version isn't available on flatpak.

There's also no AppImage version of Chromium.

**Two: Your PPA**

I added your PPA.

This actually worked for me. I get Chromium Version 91.0.4472.27 (Developer Build) Ubuntu 21.04 (64-bit). This is an old version (the latest stable version is 96.0.4664.45).

Maybe something has changed since you posted?

---

### Post by monkeybrain20122 on 2021-11-17
> **Paddy Landau said:**
> I've just tried this with Lubuntu 21.04 in a VM, and I see what you mean!

This must be Canonical's way of avoiding having to go through the process of updating its PPA all the time, which it would otherwise have to do for security reasons.

I did two things.

**One: Flatpak**

...
**Two: Your PPA**

  ...

There is also ungoogled-chromium, I think version is 95

[https://github.com/ungoogled-software/ungoogled-chromium-debian](https://github.com/ungoogled-software/ungoogled-chromium-debian)

I think OP wants Chromium because of VAAPI, but it is no longer necessary to go out of the limp to get Chromium  since VAAPI works now for all Chromium based browsers (Google-Chrome, Vivaldi, Brave-Browser, not sure about Opera--but Vivaldi is a more polished and better maintained browser anyway if one likes the opera experience) and any of those is more finished and provides better user experience than Chromium. Chromium is a perpetual beta (or alpha), at the user's end it feels like just a crippled version of Chrome, it is neither here nor there.

P.S I don't think vaapi works for either snap or flatpak.

---

### Post by Shibblet on 2021-11-17
> **monkeybrain20122 said:**
> There is also ungoogled-chromium, I think version is 95

[https://github.com/ungoogled-software/ungoogled-chromium-debian](https://github.com/ungoogled-software/ungoogled-chromium-debian)

I think OP wants Chromium because of VAAPI, but it is no longer necessary to go out of the limp to get Chromium  since VAAPI works now for all Chromium based browsers (Google-Chrome, Vivaldi, Brave-Browser, not sure about Opera--but Vivaldi is a more polished and better maintained browser anyway if one likes the opera experience) and any of those is more finished and provides better user experience than Chromium. Chromium is a perpetual beta (or alpha), at the user's end it feels like just a crippled version of Chrome, it is neither here nor there.

P.S I don't think vaapi works for either snap or flatpak.

Since I have ordered a new computer, I am going to wait until I see how much CPU usage is needed to decode H.264 or VP9 Video.  If it's under 10%, I'll probably not worry about it.
This, I believe, is ultimately where we need to go.

Remember back in the day, when MP3 Audio Decoding took like 75% of your Pentium Pro Processor?  Now, MP4 Audio can be decoded in under 1% CPU usage.
Ultimately CPU's will be able to decode video faster than co-processors.

Unless, of course, we keep doubling video into extremely unnecessary resolutions...  4K, 8K, 128K...

---

