---
title: "flash player install problems"
date: 2007-04-11
forum: General Help
---

### Post by zach12 on 2007-04-11
hi 
i am having problems with my ubuntu laptop (dell inspiron 8000 256 ram 45gbhd 800mh pros).   when i try to install flash player([http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)) the on my laptop the terminal just closes.   the download works good but the installation does not work. if i try to install a program using the ubuntu add or remove programs program it works fine. it also does not work when i tryed to install codeweavers ([http://www.codeweavers.com)/on](http://www.codeweavers.com)/on) my laptop too.
i am new at linux and need help 
thank you
:D :D :D

---

### Post by aysiu on 2007-04-11
Try this:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by zach12 on 2007-04-12
i tryed this [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) but it did not work

---

### Post by zach12 on 2007-04-12
it's a problem with the plugins directory i think

---

### Post by aysiu on 2007-04-12
> **zach12 said:**
> i tryed this [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) but it did not work
Can you be more specific?

Did you, for instance, get any error message? If so, what was the message (don't summarize it--copy and paste the exact message back here)? What command was the message in response to?

Did you not get an error message? In other words, did the installation *seem* to go well? If so, when you say "it did not work," what happens when you visit a page that requires Flash?

---

### Post by zach12 on 2007-04-12
here it is mv: cannot stat `install_flash_player_9_linux/libflashplayer.so': No such file o r directory

thank you

---

### Post by zach12 on 2007-04-12
oh sorry i hit submit too soon 
the command i used was  sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
the rest of the installation works so far 
thank you

---

### Post by aysiu on 2007-04-12
Interesting, but it didn't give you that error when you tried to move (or *mv*) the other file?

---

### Post by zach12 on 2007-04-12
yes

---

### Post by aysiu on 2007-04-12
Well, that page has a bit of hefty explanation about each command. Basically, you can do the whole thing graphically (point-and-click), but it's easier (most of the time) to just copy and paste commands into the terminal.

In your /home/zach directory or your /home/zach/Desktop directory, do you see a folder called install_flash_player_9_linux? If so, click on it. What's in that folder?

---

### Post by zach12 on 2007-04-12
do you mean in the terminal or the file browser
thank you

---

### Post by aysiu on 2007-04-12
File browser. Just click and double-click to see what folders you have an what's in 'em.

Everything we've done in the terminal is just a different way of navigating, unpacking, and moving/copying things.

---

### Post by zach12 on 2007-04-12
in the terminal or file browser

---

### Post by aysiu on 2007-04-12
File browser.

Is there a folder with the word *flash* in it? And, if so, what's inside that folder?

---

### Post by zach12 on 2007-04-12
i found the folder (install_flash_player_9_linux) in my desktop.
here is a screenshot of inside of the folder 
thank you

---

### Post by aysiu on 2007-04-12
That's weird. So the plugins are all gone. Can you go to /usr/lib/firefox/plugins and see what's in there?

Also, is Flash not working in Firefox now? Have you tried it?

---

### Post by zach12 on 2007-04-13
yes i have tryed flash and i get this error message(ERROR  You don't have the latest Shockwave x plugin.
You can download the plugin here:
[http://www.macromedia.com/shockwave/download](http://www.macromedia.com/shockwave/download))
and here is a screenshot of inside the folder (/usr/lib/firefox/plugins) 
thank you

---

### Post by zach12 on 2007-04-13
here is the screenshot

---

### Post by zach12 on 2007-04-15
i have opened the file (flashplayer-installer) useing a text progam and here it is (it's a lot of code!) thank you

#!/bin/sh
#
# Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.
#
# Adobe Flash Player Installer
#

PRODUCT="Adobe Flash Player"
VERSION="9"
PLATFORM="Linux"

FPVERSIONMAJ=9
FPVERSIONMIN=21
FPVERSIONREV=0

# Environment variables
PATH=.:/bin:/usr/bin:/usr/local/bin:/sbin:$PATH
export PATH

# Get the path of this script
cwd=`dirname $0`

# Minimum glibc
MIN_GLIBCMAJOR=2
MIN_GLIBCMINOR=2


##############################
# Subroutines
##############################

# the os is not supported
exit_os () {
  echo ""
  echo "ERROR: Your operating system is not supported by the"
  echo "       $PRODUCT installer."
  echo ""
  exit 1
}

# the architecture is not supported
exit_cpu () {
  echo ""
  echo "ERROR: Your architecture, \'$1\', is not supported by the"
  echo "       $PRODUCT installer."
  echo ""
  exit 1
}

# glibc is older than supported
exit_glibc () {
  echo ""
  echo "ERROR: Your glibc library is older than $MIN_GLIBCMAJOR.$MIN_GLIBCMINOR."
  echo "       Please update your glibc library."
  echo ""
  exit 1
}

# exit installer
exit_error () {
  echo ""
  echo "Exiting the $PRODUCT $VERSION installer."
  echo ""
  exit 1
}

# check glibc
check_glibc () {
  ICONV=`iconv --version | sed -e '2,$d'`
  if [ $? -ne 0 ]; then
    echo "no-iconv"
  else
    ICONVVER=`echo "$ICONV" | awk '{print $4}'`
    GLIBCMAJOR=`echo $ICONVVER | cut -d'.' -f1`
    GLIBCMINOR=`echo $ICONVVER | cut -d'.' -f2`
    if [ \( $GLIBCMAJOR -ge $MIN_GLIBCMAJOR \) -a \( $GLIBCMINOR -ge $MIN_GLIBCMINOR \) ]; then
      echo "valid-glibc"
    else
      echo "invalid-glibc"
    fi
  fi
}

# check entered directory
check_browser_dir () {
  CHECKDIR="$1"
  # blank?
  if [ -z "$CHECKDIR" ]; then
    echo "blank"
    exit
  fi
  # is a directory? 
  if [ -d "$CHECKDIR" ]; then
    # is writable?
    if [ -w "$CHECKDIR" ]; then
      # contains plugins and components dirs?
      if [ -d "$CHECKDIR/plugins" -a -d "$CHECKDIR/components" ]; then
        # could be Mozilla or Netscape
        if [ ! -w "$CHECKDIR/plugins" ]; then
          echo "invalid-plugins-not-writable"
          return
        else
          echo "valid"
          return
        fi
      elif [ -d "$CHECKDIR/plugins" ]; then
        if [ ! -w "$CHECKDIR/plugins" ]; then
          echo "invalid-plugins-not-writable"
          return
        fi
        # is Opera or Netscape Communicator?
        OPERABIN=`find $CHECKDIR -type f -name "opera" -print`
        if [ -f "$OPERABIN" ]; then
          echo "invalid-opera"
          return
        elif [ -f "$CHECKDIR/netscape-communicator" ]; then
          echo "valid-communicator"
          return
        fi
      fi
    else
      echo "invalid-not-writable"
      return
    fi
  else
    echo "invalid-not-directory"
    return
  fi
  echo "invalid"
}

# fix dir if necessary
fix_dir () {
  FIXDIR="$1"
  FIRSTCHAR=`expr "$FIXDIR" : '\(.\).*'`
  if [ "$FIRSTCHAR" != '/' ]; then
    currentdir=`pwd`
    echo "$currentdir/$FIXDIR"
  else
    echo "$1"
  fi
}

# warn libflashplayer.so is a symbolic link
warn_symbolic_link () {
  echo ""
  echo "WARNING: The $PRODUCT binary is a symbolic link."
  echo "         The installer will replace this symbolic link with the actual binary."
  echo ""
}

# compare versions
compare_versions () {
  BIN="$1"
  MYFPVERSIONSTR=`strings "$1" | grep -e "^Shockwave Flash [.\d+]*" | sed -e "s/Shockwave Flash //g"`
  MYFPVERSION=`echo "$MYFPVERSIONSTR" | awk '{print $1}'`
  MYFPVERSIONMAJ=`echo "$MYFPVERSION" | cut -d'.' -f1`
  MYFPVERSIONMIN=`echo "$MYFPVERSION" | cut -d'.' -f2`
  MYFPVERSIONREV=`echo "$MYFPVERSIONSTR" | awk '{print $2}' | sed -e "s/^r//g"`
  # check major version
  if [ \( $MYFPVERSIONMAJ -lt $FPVERSIONMAJ \) ]; then
    echo "version-older"
  elif [ \( $MYFPVERSIONMAJ -gt $FPVERSIONMAJ \) ]; then
    echo "version-newer"
  elif [ \( $MYFPVERSIONMAJ -eq $FPVERSIONMAJ \) ]; then
    # check minor version
    if [ \( $MYFPVERSIONMIN -lt $FPVERSIONMIN \) ]; then
      echo "version-older"
    elif [ \( $MYFPVERSIONMIN -gt $FPVERSIONMIN \) ]; then
      echo "version-newer"
    elif [ \( $MYFPVERSIONMIN -eq $FPVERSIONMIN \) ]; then
      # check rev version
      if [ \( $MYFPVERSIONREV -lt $FPVERSIONREV \) ]; then
        echo "version-older"
      elif [ \( $MYFPVERSIONREV -gt $FPVERSIONREV \) ]; then
        echo "version-newer"
      elif [ \( $MYFPVERSIONREV -eq $FPVERSIONREV \) ]; then
        echo "version-same"
      fi
    fi
  fi
}

# check plugins dir
check_plugins_dir () {
  CHECKPLUGINSDIR="$1"
  if [ -d "$CHECKPLUGINSDIR" ]; then
    # does it exist?
    if [ -e "$CHECKPLUGINSDIR/libflashplayer.so" ]; then
      # is it a file?
      if [ -f "$CHECKPLUGINSDIR/libflashplayer.so" ]; then
        # is it a symbolic link?
        if [ -L "$CHECKPLUGINSDIR/libflashplayer.so" ]; then
          warn_symbolic_link "$CHECKPLUGINSDIR/libflashplayer.so"
          SYMBOLIC_LINK=1
        else
          VERSIONSTATUS=`compare_versions "$CHECKPLUGINSDIR/libflashplayer.so"`
          case $VERSIONSTATUS in
            version-older)
              echo ""
              echo "WARNING: An older version of the $PRODUCT has been detected in"
              echo "         $CHECKPLUGINSDIR."
              echo "         The installer will overwrite this existing binary."
              echo ""
              ;;
            version-newer)
              echo ""
              echo "WARNING: A newer version of the $PRODUCT has been detected in"
              echo "         $CHECKPLUGINSDIR."
              echo "         The installer will overwrite this existing binary."
              echo ""
              ;;
            version-same)
              echo ""
              echo "WARNING: The same version of the $PRODUCT has been detected in"
              echo "         $CHECKPLUGINSDIR."
              echo "         The installer will overwrite this existing binary."
              echo ""
              ;;
          esac
        fi
      fi
    fi
  fi
}


##############################
# Main Section
##############################

ROOTINSTALL=0

# check user
USERID=`id | sed -e 's/).*//; s/^.*(//;'`
if [ "X$USERID" = "Xroot" ]; then
  ROOTINSTALL=1
fi

# check OS
os=`uname -s`
if [ "X$os" != "XLinux" ]; then
  exit_os
fi

# check architecture
TEMPARCH=`uname -m`
case $TEMPARCH in
  i[3456]86)
    ARCH=i386
    ;;
  *)
    exit_cpu $TEMPARCH
    ;;
esac

# check for iconv and version of glibc
GLIBCSTATUS=`check_glibc`
case $GLIBCSTATUS in
  invalid-glibc)
    exit_glibc
    ;;
esac

##################
# Welcome user
##################
echo ""
echo "Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved."
echo ""
echo "$PRODUCT $VERSION for $PLATFORM"
echo ""
echo "$PRODUCT $VERSION will be installed on this machine."
echo ""
if [ $ROOTINSTALL -eq 1 ]; then
echo "You are running the $PRODUCT installer as the \"root\" user."
echo "$PRODUCT $VERSION will be installed system-wide."
else
echo "You are running the $PRODUCT installer as a non-root user."
echo "$PRODUCT $VERSION will be installed in your home directory."
fi
echo ""
echo "Support is available at http://www.adobe.com/support/flashplayer/"
echo ""
echo "To install $PRODUCT $VERSION now, press ENTER."
echo ""
echo "To cancel the installation at any time, press Control-C."
echo ""
read cont < /dev/tty

echo ""
echo "NOTE: Please exit any browsers you may have running."
echo ""
echo "Press ENTER to continue..."
echo ""
read cont < /dev/tty

# Loop until user is done installing one or more times
okToRepeat=0
while [ $okToRepeat -eq 0 ]; do

# Loop until user is comfortable with their choices
okToProceed=0
while [ $okToProceed -eq 0 ]; do

  # default variables
  BROWSERDIR=""
  DIRSTATUS=""
  HOMEDIR=""
  MOZILLA=0
  MOZILLADIR=""
  MOZILLA_NOT_W=0
  MOZILLAPLUGIN_NOT_W=0
  MOZILLASTATUS="valid"
  NETSCAPE=0
  NETSCAPEDIR=""
  NETSCAPE_NOT_W=0
  NETSCAPEPLUGIN_NOT_W=0
  NETSCAPESTATUS="valid"
  OPERA=0
  OPERADIR=""
  OPERA_NOT_W=0
  OPERAPLUGIN_NOT_W=0
  OPERASTATUS="valid"
  SYMBOLIC_LINK=0
  VERSIONSTATUS=0

  ############################
  # Get destination directory
  ############################
  echo ""
  get_browser_dir () {
    echo "Please enter the installation path of the Mozilla, SeaMonkey,"
    printf "or Firefox browser (i.e., /usr/lib/mozilla): "
    read dir

    # fix the entered dir if necessary
    FIXED_DIR=`fix_dir "$dir"`
    dir="$FIXED_DIR"

	echo "dir= $dir"
    # check given dir if valid
    DIRSTATUS=`check_browser_dir "$dir"`

    case $DIRSTATUS in
      blank)
        echo ""
        echo "WARNING: Please do not enter a blank installation path."
        echo ""
        get_browser_dir
        ;;
      invalid)
        echo ""
        echo "WARNING: Please enter a valid installation path."
        echo ""
        get_browser_dir
        ;;
      invalid-not-writable)
        echo ""
        echo "WARNING: $dir is not writable."
        echo ""
        get_browser_dir
        ;;
      invalid-plugins-not-writable)
        echo ""
        echo "WARNING: $dir/plugins is not writable."
        echo ""
        get_browser_dir
        ;;
      invalid-not-directory)
        echo ""
        echo "WARNING: $dir is not a directory."
        echo ""
        get_browser_dir
        ;;
      valid)
        BROWSERDIR="$dir"
        check_plugins_dir "$dir/plugins"
        ;;
      valid-communicator)
        echo ""
        echo "WARNING: You have entered the installation path to Netscape Communicator."
        echo "         Netscape Communicator is not officially supported."
        echo ""
        NETSCAPE=1
        BROWSERDIR="$dir"
        check_plugins_dir "$dir/plugins"
        ;;
      invalid-opera)
        echo ""
        echo "ERROR: Opera is not supported."
        echo ""
        exit 1
        ;;
    esac
  }
  if [ $ROOTINSTALL -eq 1 ]; then
    get_browser_dir
  else
    HOMEDIR=`(cd ; pwd)`
    COUNT=0
    STATUSCOUNT=0
    ERRORCOUNT=0
    # Mozilla user directory
    if [ -d "$HOMEDIR/.mozilla" ]; then
      MOZILLA=1
      MOZILLADIR="$HOMEDIR/.mozilla"
      COUNT=`expr $COUNT + 1`
      if [ ! -w "$HOMEDIR/.mozilla" ]; then
        MOZILLA_NOT_W=1
        MOZILLASTATUS="invalid"
        ERRORCOUNT=`expr $ERRORCOUNT + 1`
      elif [ \( -d "$HOMEDIR/.mozilla/plugins" \) -a \( ! -w "$HOMEDIR/.mozilla/plugins" \) ]; then
        MOZILLAPLUGIN_NOT_W=1
        MOZILLASTATUS="invalid"
        ERRORCOUNT=`expr $ERRORCOUNT + 1`
      else
        STATUSCOUNT=`expr $STATUSCOUNT + 1`
      fi
    fi
    # Netscape user directory
    if [ -d "$HOMEDIR/.netscape" ]; then
      NETSCAPE=1
      NETSCAPEDIR="$HOMEDIR/.netscape"
      COUNT=`expr $COUNT + 1`
      if [ ! -w "$HOMEDIR/.netscape" ]; then
        NETSCAPE_NOT_W=1
        NETSCAPESTATUS="invalid"
        ERRORCOUNT=`expr $ERRORCOUNT + 1`
      elif [ \( -d "$HOMEDIR/.netscape/plugins" \) -a \( ! -w "$HOMEDIR/.netscape/plugins" \) ]; then
        NETSCAPEPLUGIN_NOT_W=1
        NETSCAPESTATUS="invalid"
        ERRORCOUNT=`expr $ERRORCOUNT + 1`
      else
        STATUSCOUNT=`expr $STATUSCOUNT + 1`
      fi
    fi
    if [ \( $MOZILLA -eq 0 \) -a \( $NETSCAPE -eq 0 \) -a \( $OPERA -eq 0 \) ]; then
      echo ""
      echo "ERROR: Your home directory does not have a Mozilla, SeaMonkey or Firefox"
      echo "       browser user directory. Run one of these browsers at least once."
      echo ""
      exit 1
    fi
  fi

  # if local install, ask which dirs to install to if more than one
  if [ $ROOTINSTALL -ne 1 ]; then
    if [ \( $COUNT -gt 1 \) -a \( $STATUSCOUNT -gt 1 \) ]; then
      echo ""
      echo "Please choose which directory to install $PRODUCT $VERSION:"
      echo ""
      if [ $MOZILLA -eq 1 ]; then
        if [ "$MOZILLASTATUS" = "valid" ]; then
        echo "  [m] Install $PRODUCT $VERSION into Mozilla user"
        echo "      directory: $MOZILLADIR"
        else
        echo "   *  The installer has detected a Mozilla user directory but cannot install"
        echo "      into the following path: $MOZILLADIR"
        echo "      because of the following:"
        fi
        if [ $MOZILLA_NOT_W -eq 1 ]; then
        echo ""
        echo "      WARNING: $MOZILLADIR is not writable."
        fi
        if [ \( $MOZILLA_NOT_W -eq 0 \) -a \( $MOZILLAPLUGIN_NOT_W -eq 1 \) ]; then
        echo ""
        echo "      WARNING: $MOZILLADIR/plugins is not writable."
        fi
        echo ""
      fi
      if [ $NETSCAPE -eq 1 ]; then
        if [ "$NETSCAPESTATUS" = "valid" ]; then
        echo "  [n] Install $PRODUCT $VERSION into Netscape user"
        echo "      directory: $NETSCAPEDIR"
        else
        echo "   *  The installer has detected a Netscape user directory but cannot install"
        echo "      into the following path: $NETSCAPEDIR"
        echo "      because of the following:"
        fi
        if [ $NETSCAPE_NOT_W -eq 1 ]; then
        echo ""
        echo "      WARNING: $NETSCAPEDIR is not writable."
        fi
        if [ \( $NETSCAPE_NOT_W -eq 0 \) -a \( $NETSCAPEPLUGIN_NOT_W -eq 1 \) ]; then
        echo ""
        echo "      WARNING: $NETSCAPEDIR/plugins is not writable."
        fi
        echo ""
      fi
      echo "  [a] All"
      echo ""
    else
      # only one browser user directory
      if [ $MOZILLA -eq 1 ]; then
        if [ "$MOZILLASTATUS" = "invalid" ]; then
          echo "The installer has detected a Mozilla user directory but cannot install"
          echo "into the following path: $MOZILLADIR"
          echo "because of the following:"
          if [ $MOZILLA_NOT_W -eq 1 ]; then
            echo ""
            echo "WARNING: $MOZILLADIR is not writable."
            echo ""
          fi
          if [ \( $MOZILLA_NOT_W -eq 0 \) -a \( $MOZILLAPLUGIN_NOT_W -eq 1 \) ]; then
            echo ""
            echo "WARNING: $MOZILLADIR/plugins is not writable."
            echo ""
          fi
        fi
      fi
      if [ $NETSCAPE -eq 1 ]; then
        if [ "$NETSCAPESTATUS" = "invalid" ]; then
          echo "The installer has detected a Netscape user directory but cannot install"
          echo "into the following path: $NETSCAPEDIR"
          echo "because of the following:"
          if [ $NETSCAPE_NOT_W -eq 1 ]; then
            echo ""
            echo "WARNING: $NETSCAPEDIR is not writable."
            echo ""
          fi
          if [ \( $NETSCAPE_NOT_W -eq 0 \) -a \( $NETSCAPEPLUGIN_NOT_W -eq 1 \) ]; then
            echo ""
            echo "WARNING: $NETSCAPEDIR/plugins is not writable."
            echo ""
          fi
        fi
      fi 
    fi
  fi
  select_local_install () {
    printf "Please choose a directory: "
    read inum

    if [ \( \( "$inum" = "m" \) -o \( "$inum" = "M" \) \) -a \( \( $MOZILLA -eq 1 \) -a \( "$MOZILLASTATUS" = "valid" \) \) ]; then
      NETSCAPE=0
      OPERA=0
      check_plugins_dir "$MOZILLADIR/plugins"
    elif [ \( \( $NETSCAPE -eq 1 \) -a \( "$NETSCAPESTATUS" = "valid" \) \) -a \( \( "$inum" = "n" \) -o \( "$inum" = "N" \) \) ]; then
      MOZILLA=0
      OPERA=0
      check_plugins_dir "$NETSCAPEDIR/plugins"
    elif [ \( "$inum" = "a" \) -o \( "$inum" = "A" \) ]; then
      # do nothing
      NOTHING=1
      if [ \( $MOZILLA -eq 1 \) -a \( "$MOZILLASTATUS" = "valid" \) ]; then
        check_plugins_dir "$MOZILLADIR/plugins"
      fi
      if [ \( $NETSCAPE -eq 1 \) -a \( "$NETSCAPESTATUS" = "valid" \) ]; then
        check_plugins_dir "$NETSCAPEDIR/plugins"
      fi
    else
      echo ""
      echo "ERROR: Please choose a directory from the list."
      echo ""
      select_local_install
    fi
  }
  if [ $ROOTINSTALL -ne 1 ]; then
    if [ \( $COUNT -gt 1 \) -a \( $STATUSCOUNT -gt 1 \) ]; then
      select_local_install
    fi
    if [ $COUNT -eq $ERRORCOUNT ]; then
      exit_error
    fi
  fi


  ##########
  # Summary
  ##########
  echo ""
  echo ""
  echo "----------- Install Action Summary -----------"
  echo ""
  echo "$PRODUCT $VERSION will be installed in the following directory:"
  echo ""
  if [ $ROOTINSTALL -eq 1 ]; then
    echo "Browser installation directory = $BROWSERDIR"
  else
    if [ \( $MOZILLA -eq 1 \) -a \( "$MOZILLASTATUS" = "valid" \) ]; then
      echo "Mozilla installation directory  = $MOZILLADIR"
    fi
    if [ \( $NETSCAPE -eq 1 \) -a \( "$NETSCAPESTATUS" = "valid" \) ]; then
      echo "Netscape installation directory = $NETSCAPEDIR"
    fi
  fi
  echo ""

  # okay to continue?
  get_installagreement () {
    printf 'Proceed with the installation? (y/n/q): '
    read yn

    case $yn in
      y | Y)
        okToProceed=1
        ;;
      n | N)
        continue
        ;;
      q | Q)
        exit 1
        ;;
      *)
        echo ""
        echo "Please enter 'y', 'n', or 'q'."
        get_installagreement
        ;;
    esac
  }
  get_installagreement

done


#######################
# Perform installation
#######################

#--------------
# copy plug-in
#--------------
# system-wide
if [ $ROOTINSTALL -eq 1 ]; then
  # copy plug-in
  # remove symbolic link before copying
  if [ $SYMBOLIC_LINK -eq 1 ]; then
    rm -f "$BROWSERDIR/plugins/libflashplayer.so"
  fi
  cp -f "$cwd/libflashplayer.so" "$BROWSERDIR/plugins"
else
# local
  if [ $MOZILLA -eq 1 ]; then
    if [ \( ! -d "$MOZILLADIR/plugins" \) -a \( $MOZILLA_NOT_W -eq 0 \) ]; then
      mkdir -p "$MOZILLADIR/plugins"
    fi
    if [ \( $MOZILLA_NOT_W -eq 0 \) -a \( $MOZILLAPLUGIN_NOT_W -eq 0 \) ]; then
      cp -f "$cwd/libflashplayer.so" "$MOZILLADIR/plugins"
    fi
  fi
  if [ $NETSCAPE -eq 1 ]; then
    if [ \( ! -d "$NETSCAPEDIR/plugins" \) -a \( $NETSCAPE_NOT_W -eq 0 \) ]; then
      mkdir -p "$NETSCAPEDIR/plugins"
    fi
    if [ \( $NETSCAPE_NOT_W -eq 0 \) -a \( $NETSCAPEPLUGIN_NOT_W -eq 0 \) ]; then
      cp -f "$cwd/libflashplayer.so" "$NETSCAPEDIR/plugins"
    fi
  fi
fi

#----------------------
# remove xpti.dat file
#----------------------
if [ $ROOTINSTALL -eq 1 ]; then
  if [ -f "$BROWSERDIR/components/xpti.dat" ]; then
    rm -f "$BROWSERDIR/components/xpti.dat"
  fi
else
  if [ \( $MOZILLA -eq 1 \) -o \( $NETSCAPE -eq 1 \) ]; then
    # don't know where xpti.dat file is located
    echo ""
    echo "NOTE: Please ask your administrator to remove the xpti.dat from the"
    echo "      components directory of the Mozilla or Netscape browser."
    echo ""
  fi
fi

#-----------------
# set permissions
#-----------------
if [ $ROOTINSTALL -eq 1 ]; then
  chmod 755 "$BROWSERDIR/plugins/libflashplayer.so"
else
  if [ $MOZILLA -eq 1 ]; then
    if [ \( $MOZILLA_NOT_W -eq 0 \) -a \( $MOZILLAPLUGIN_NOT_W -eq 0 \) ]; then
      chmod 755 "$MOZILLADIR/plugins/libflashplayer.so"
    fi
  fi
  if [ $NETSCAPE -eq 1 ]; then
    if [ \( $NETSCAPE_NOT_W -eq 0 \) -a \( $NETSCAPEPLUGIN_NOT_W -eq 0 \) ]; then
      chmod 755 "$NETSCAPEDIR/plugins/libflashplayer.so"
    fi
  fi
fi

echo ""
echo "Installation complete."
echo ""

# Ask to repeat installation?
ask_to_repeat () {
  echo ""
  printf 'Perform another installation? (y/n): '
  read yn

  case $yn in
    y | Y)
      continue
      ;;
    n | N)
      okToRepeat=1
      break
      ;;
    *)
      echo ""
      echo "Please enter 'y' or 'n'."
      ask_to_repeat
      ;;
  esac
}
ask_to_repeat

done

# Final messages.

# check MOZ_PLUGIN_PATH
if [ ! -z "$MOZ_PLUGIN_PATH" ]; then
  echo ""
  echo "WARNING: You have the MOZ_PLUGIN_PATH environment variable set."
  echo "         Either unset this environment variable or set the path in this"
  echo "         environment variable to the path you are installing the plug-in."
  echo ""
fi

echo ""
echo ""
echo "Please log out of this session and log in for the changes to take effect."
echo ""

echo ""
echo "The $PRODUCT installation is complete."
echo ""

---

### Post by mimsmall on 2007-04-16
Just this afternoon I put the tar.gz file from the  Adobe download page on my Dapper Drake laptop. I just followed the instructions Adobe recommends. I've read the whole thread and am not sure what the problem that you are having.

---

### Post by jdong on 2007-04-16
Any reason why installing from the repositories doesn't work? (sudo apt-get install flashplugin-nonfree)

In the official Dapper and Edgy Backports repositories, I have approved Flash version 9.

```

flashplugin-nonfree | 9.0.31.0.1ubuntu1~dapper1 | dapper-backports/multiverse | source, i386
flashplugin-nonfree | 9.0.31.0.1ubuntu1~edgy1 | edgy-backports/multiverse | source, i386
flashplugin-nonfree | 9.0.31.0.2ubuntu1 | feisty/multiverse | source, i386

```

---

### Post by zach12 on 2007-04-17
firefox does not run flash player apps and i get a error message 
and when i try to install flash(sudo apt-get install flashplugin-nonfree) i get this error message (flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.) and i tryed flash
and it does not work
thank you for help
:D

---

### Post by Sef on 2007-04-17
> firefox does not run flash player apps and i get a error message 

What error message do you get?

> and when i try to install flash(sudo apt-get install flashplugin-nonfree) i get this error message (flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.) 

You have the latest flash already.  Have you tried to uninstall flash, then reinstall it from multiverse?

---

### Post by raptor2552 on 2007-04-17
The easy way to install flash is to open Firefox, browse to youtube.com and it will ask you if you want to install flash.

I think shockwave is the activex flash control used by windows ie and will not work on ubuntu.

---

### Post by zach12 on 2007-04-17
i tryed to do that but that is why posted this problem here is the error (ERROR : You don't have the latest Shockwave x plugin.

You can download the plugin here:
[http://www.macromedia.com/shockwave/download](http://www.macromedia.com/shockwave/download)

Upon successful installation, please restart your computer, reload this game, and enjoy! Contact the customer support of [www.macromedia.com](www.macromedia.com) for any issues with upgrading this plugin.)
and problem i am haveing is that when i download any progam useing firefox it does not install Right (does not work)
thank you

---

### Post by zach12 on 2007-04-17
ps i am installing  flash 9

---

### Post by jdong on 2007-04-17
Whoa... does your website need **Shockwave** or **Flash**? These are very different technologies, of which there is no Shockwave plugin for Linux.

To test if Flash works, go to youtube and try to watch a video (I know, it's painful. My friends have forced me to bear through that Shoes video and that singing crocodile cartoon and whatnot, now you have to, too.)

---

### Post by zach12 on 2007-04-18
utube videos worked good.  here is the link to what i have this problem with [http://www.neopets.com/games/play.phtml?game_id=349](http://www.neopets.com/games/play.phtml?game_id=349). i also am haveing problems with any download they do not install at all.
thank you

---

### Post by jdong on 2007-04-18
That is a shockwave video, and currently Adobe has not released any support for Shockwave under Linux. Supposedly it is possible to do something with Crossover or WINE to get it to work, but I've yet to try it.

---

### Post by akshaysrinivasan on 2007-04-18
You can manually install the plugins if you want to.Just move the libflashplayer.so and flashplayer.xpt to /usr/lib/firefox/plugins .

---

### Post by jdong on 2007-04-18
> **akshaysrinivasan said:**
> You can manually install the plugins if you want to.Just move the libflashplayer.so and flashplayer.xpt to /usr/lib/firefox/plugins .
That will still do him no good; he's trying to play a shockwave file... (His Flash9 already works, as youtube works.)

---

### Post by zach12 on 2007-04-18
do you have any ideas on how to get it to work

---

### Post by zach12 on 2007-04-21
thank you

---

