---
title: "Acroread Installation"
date: 2005-05-22
forum: General Help
---

### Post by larry on 2005-05-22
Hi everybody,
I recently installed acroread from multiverse. I have a trivial problem, but I am a newbiw and I do not know how to fix it.
When I try launching the program, this is what I get:

larry@ubuntu:~ $ acroread
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory

Acroread is installed in the directory:

/usr/lib/Acrobat5/Reader/intellinux/bin

I looked up the script in /usr/bin/acroread that is:

#!/bin/sh


LANG=${LANG%@euro}
LC_CTYPE=${LC_CTYPE%@euro}
LC_ALL=${LC_ALL%@euro}
LANG=${LANG%.UTF-8}
LC_CTYPE=${LC_CTYPE%.UTF-8}
LC_ALL=${LC_ALL%.UTF-8}

umask 077
/usr/lib/Acrobat5/bin/acroread "$@"

I tried replacing the last line with:

/usr/lib/Acrobat5/Reader/intellinux/bin/acroread "$@"

but everything I get is:

/usr/lib/Acrobat5/Reader/intellinux/bin/acroread must be executed from the startup script.


There is another long script in /usr/lib/Acrobat5/bin which may have something to do with it.
I attach the file (sorry for the long post).
I am sure it must be a matter of adding the right line somewhere, but I do not know where!
Cheers
Larry




#!/bin/sh
#

ver=5.0.10
install_dir=REPLACE_ME

#
# Prepend a colon separated environment variable
# $1 string to be prepended
# $2 environment variable
#
prepend()
{
  if [ -z "$2" -o "$2" = "$1" ] ; then
    echo "$1"
  else
    first="`expr "$2" : '\([^:]*\):'`"
    if [ "$first" = "$1" ] ; then
      echo "$2"
    else
      echo "${1}:${2}"
    fi
  fi
}


#
# Tests the version file in an installation directory.
#
test_install_dir()
{
  if [ "$1" -a -f "$1/AcroVersion" ] \
  && [ "`cat $1/AcroVersion 2>/dev/null`" = "$ver" ] ; then
    return 0
  else
    return 1
  fi
}


#
# Get the current working directory.
# Try to avoid automounter directories by checking
# if $HOME or $PWD is the same directory as pwd,
# and removing the automount directory component.
#
cwd="`pwd 2> /dev/null`"
if [ -z "$cwd" -o ! -d "$cwd" ] ; then
  echo "ERROR: Cannot determine current directory."
  exit 1
fi

if [ "$HOME" -a -d "$HOME" ] && [ "`cd / ; cd "$HOME" ; pwd`" = "$cwd" ] ; then
  cwd="$HOME"
elif [ "$PWD" -a -d "$PWD" ] && [ "`cd / ; cd "$PWD" ; pwd`" = "$cwd" ] ; then
  cwd="$PWD"
fi

if [ "$cwd" != / -a "${AUTOMOUNT_DIR=/tmp_mnt}" ] ; then
  tmp="`expr "$cwd" : "$AUTOMOUNT_DIR"'\(.*\)'`"
  if [ "$tmp" -a -d "$tmp" ] ; then
    if [ "`cd / ; cd "$tmp" ; pwd`" = "`pwd`" ] ; then
      cwd="$tmp"
    fi
  fi
fi

PWD="$cwd"
export PWD


#
# Setup ACRO_ARG0 to this script
#
arg0="$0"
if [ "$arg0" ] ; then
  case "$arg0" in
     /*) ;;
    ./*) arg0="$cwd/`expr "$arg0" : '\./\(.*\)'`" ;;
      *) arg0="$cwd/$arg0" ;;
  esac

  ACRO_ARG0="$arg0"
  export ACRO_ARG0
fi


#
# Try to find the installation directory
#
if ( test_install_dir "$install_dir" ) ; then
  ACRO_INSTALL_DIR="$install_dir"
  export ACRO_INSTALL_DIR
else
  script="$arg0"
  while [ "$script" ] ; do
    install_dir="`dirname "$script"`"
    if ( test_install_dir "$install_dir" ) ; then
      ACRO_INSTALL_DIR="$install_dir"
      export ACRO_INSTALL_DIR
      break
    fi

    install_dir="`dirname "$install_dir"`"
    if ( test_install_dir "$install_dir" ) ; then
      ACRO_INSTALL_DIR="$install_dir"
      export ACRO_INSTALL_DIR
      break
    fi

    if [ -h "$script" ] ; then
      new_script=`ls -l "$script" | sed 's/^.*-> *\(.*\) *$/\1/'`
      if [ "$new_script" -a "`expr "$new_script" : '/.*'`" = 0 ] ; then
        new_script="`dirname "$script"`/$new_script"
      fi
      script="$new_script"
    else
      break
    fi
  done

  if ( test_install_dir "$ACRO_INSTALL_DIR" ) ; then
    :
  elif ( test_install_dir "$ACRO_HOME" ) ; then
    ACRO_INSTALL_DIR="$ACRO_HOME"
    export ACRO_INSTALL_DIR
  else
    echo "ERROR: Cannot find installation directory."
    exit 1
  fi
fi


#
# setup the configuration from uname
#
os_name=`uname -s`
if [ "$os_name" = "AIX" ] ; then
  os_release=`uname -a | ( read name host minor major foo ; echo $major.$minor )`
else
  os_release=`uname -r`
fi

case "$os_name" in
  SunOS)
    case "$os_release" in
      4.1.3*|4.1.4*|4.1C)
        ACRO_CONFIG=sparcsun
        export ACRO_CONFIG
        ;;
      5.*)
        machine_type=`uname -p`
        case "$machine_type" in
          sparc)
            ACRO_CONFIG=sparcsolaris
            export ACRO_CONFIG
            ;;
          intel|i386)
            ACRO_CONFIG=intelsolaris
            export ACRO_CONFIG
            ;;
          ppc)
            ACRO_CONFIG=ppcsolaris
            export ACRO_CONFIG
            ;;
        esac
        ;;
    esac
    ;;
  HP-UX)
    case "$os_release" in
      *09.0*|*10.*|*11.*)
        ACRO_CONFIG=hppahpux
        export ACRO_CONFIG
        ;;
      *)
        ;;
    esac
    ;;
  AIX)
    case "$os_release" in
      4.*|5.*)
        ACRO_CONFIG=rs6000aix
        export ACRO_CONFIG
        ;;
      *)
        ;;
    esac
    ;;
   Linux)
    ACRO_CONFIG=intellinux
    export ACRO_CONFIG
    ;;
esac

if [ -z "$ACRO_CONFIG" ] ; then
  echo "The OS named $os_name version $os_release is currently not installed."
  echo "Try running on an installed platform and connecting to your display."
  echo "Installed platform(s) include the following:"
  if [ -d "$ACRO_INSTALL_DIR"/sparcsolaris ] ; then
    echo "  SPARC/Solaris version 2.x"
  fi
  if [ -d "$ACRO_INSTALL_DIR"/hppahpux ] ; then
    echo "  HP/HP-UX version 9.0.x and 10.x"
  fi
  if [ -d "$ACRO_INSTALL_DIR"/rs6000aix ] ; then
    echo "  RS6000/AIX version 4.1.1, 4.2, 4.3, and 5.1"
  fi
  if [ -d "$ACRO_INSTALL_DIR"/intellinux ] ; then
    echo "  Intel/Linux"
  fi
  exit 1
fi

#
# Setup XKEYSYMDB
#
if [ -z "$XKEYSYMDB" -o ! -f "$XKEYSYMDB" ] ; then
  if [ -f "$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib/XKeysymDB" ] ; then
    XKEYSYMDB="$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib/XKeysymDB"
    export XKEYSYMDB
  elif [ -f "$ACRO_INSTALL_DIR/XKeysymDB" ] ; then
    XKEYSYMDB="$ACRO_INSTALL_DIR/XKeysymDB"
    export XKEYSYMDB
  fi
fi


#
# Prepend XFILESEARCHPATH
#
XFILESEARCHPATH="`prepend "$ACRO_INSTALL_DIR/$ACRO_CONFIG/%T/%L/%N%S:$ACRO_INSTALL_DIR/$ACRO_CONFIG/%T/%l/%N%S:$ACRO_INSTALL_DIR/$ACRO_CONFIG/%T/%N%S" "$XFILESEARCHPATH"`"
export XFILESEARCHPATH

#
# Setup configuration specific environment variables
#
case "$ACRO_CONFIG" in
  sparcsolaris)
    LD_LIBRARY_PATH="`prepend "$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib:$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib" "$LD_LIBRARY_PATH"`"
    export LD_LIBRARY_PATH
    if [ -z "$LC_CTYPE" ] ; then
      LC_CTYPE="iso_8859_1"
      export LC_CTYPE
    fi
    ;;
  hppahpux)
    SHLIB_PATH="`prepend "$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib:$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib" "$SHLIB_PATH"`"
    SHLIB_PATH="`prepend "/usr/lib/Motif1.2" "$SHLIB_PATH"`"
    SHLIB_PATH="`prepend "/usr/lib/X11R5" "$SHLIB_PATH"`"
    export SHLIB_PATH
    ;;
  rs6000aix)
    LIBPATH="`prepend "$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib:$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib" "$LIBPATH"`"
    export LIBPATH
    XNLSPATH=/usr/lib/X11/nls
    export XNLSPATH
    ;;
  intellinux)
    LD_LIBRARY_PATH="`prepend "$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib:$ACRO_INSTALL_DIR/$ACRO_CONFIG/lib" "$LD_LIBRARY_PATH"`"
    export LD_LIBRARY_PATH
    unset LC_ALL
    unset LC_CTYPE
    LANG="C"
    export LANG
    ;;
esac

DefaultPSRESPATH="$HOME/psres:$HOME/fonts:/usr/psres:$ACRO_INSTALL_DIR/$ACRO_CONFIG/fonts"
if [ -z "$PSRESOURCEPATH" ] ; then
  PSRESOURCEPATH="$DefaultPSRESPATH"
else
  PSRESOURCEPATH="$PSRESOURCEPATH":"$DefaultPSRESPATH"
fi
case "$PSRESOURCEPATH" in
  ::*|*::*|*::)
    ;;
  *)
    PSRESOURCEPATH="$PSRESOURCEPATH"::
    ;;
esac
export PSRESOURCEPATH

directory="`basename \"$ACRO_INSTALL_DIR\"`"
case "$directory" in
  Reader)
    cmd="acroread"
    prod="Acrobat Reader"
    ;;
  *)
    cmd="acrobat"
    prod="Acrobat 5.0"
    ;;
esac

#
# Set the command.  Process any debug flags and exec.
#
ACRO_EXEC_CMD="$ACRO_INSTALL_DIR/$ACRO_CONFIG/bin/$cmd"

if [ "$1" = "-DEBUG" ] ; then
  if [ $# = 1 ] ; then
    export ACRO_EXEC_CMD
    exec "$SHELL"
  else
    shift
    exec ${1+"$@"} "$ACRO_EXEC_CMD"
  fi
fi

if [ -f "$ACRO_EXEC_CMD" ] ; then
  exec "$ACRO_EXEC_CMD" ${1+"$@"}
else
  echo "ERROR: Cannot find $ACRO_EXEC_CMD"
  echo "  $prod not installed for this configuration, \"$ACRO_CONFIG\"."
  exit 1
fi

---

### Post by Xian on 2005-05-22
You could set up a sym link in /usr/bin, but I would think you'd be better off just installing Adobe Reader from source at their home page for a couple of reasons. The version you installed in APT is 5.x and the current version available in 7.x. Also, I have a feeling that the shell script in /usr/lib/Acrobat5/bin/ will have difficulty finding the installation directory.

---

### Post by FreeEagle on 2005-05-22
hi there ... i will help you... and this is the solution to your Problem and it will work like a charm


[http://www.ubuntulinux.org/wiki/AcrobatHowTo](http://www.ubuntulinux.org/wiki/AcrobatHowTo)


Best Regards,
 FreeEagle

---

### Post by Xian on 2005-05-22
Nice. I thought that install dir issue would exist.
Here's a fast mirror if you want to use the 7.0 Adobe Reader: [AA-7.0](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/AdbeRdr70_linux_enu.tar.gz)

---

### Post by larry on 2005-05-22
Thanks to you both. Now it works.
I have to say that Ubuntu's community is its main selling point; so far I have always fund people ready to give a hand even when I come up with trivial problems.
As to installing the software from source, that is another thing I need to learn at some stage.
Is there a standard procedure? I heard somewhere that Debian is clumsy when you want to compile things from source, if that is true I fear it will be the same for Ubuntu.
Cheers
Larry

---

### Post by Xian on 2005-05-22
[QUOTE=larry]Is there a standard procedure? I heard somewhere that Debian is clumsy when you want to compile things from source, if that is true I fear it will be the same for Ubuntu.[/QUOTE]
There is somewhat of a standard procedure: [Installing Software](http://www.tuxfiles.org/linuxhelp/softinstall.html). But the Adobe Reader is not a source file that has to be compiled. It just goes into an installation directory that can be used by the host system for its intended purpose. It is very similar to when you would install Java on your machine.

---

### Post by FreeEagle on 2005-05-22
you welcome ....


FreeEagle

---

### Post by bored2k on 2005-05-22
[QUOTE=Xian]There is somewhat of a standard procedure: [Installing Software](http://www.tuxfiles.org/linuxhelp/softinstall.html). But the Adobe Reader is not a source file that has to be compiled. It just goes into an installation directory that can be used by the host system for its intended purpose. It is very similar to when you would install Java on your machine.[/QUOTE]
 It's also in Marillat's. That's the only use for those repositories right now..

---

