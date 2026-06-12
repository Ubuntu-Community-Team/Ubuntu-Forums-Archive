---
title: "Permission Denied error when running installation script"
date: 2014-03-23
forum: General Help
---

### Post by sarosh2 on 2014-03-23
Hello I am trying to run an installation script (.sh) using the command [COLOR=#000000]GTTEMPDIR=/media/sarosh/Data/GTIse/GTTEMPD sh cdinstall.sh but I keep getting this error:

[/COLOR]```
[COLOR=#000000]Creating temporary install directory: /media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565[/COLOR]


[COLOR=#000000]To change the temporary directory for the installer, please cancel[/COLOR]
[COLOR=#000000]the installer, export GTTEMPDIR=SomeTempDir, and restart the installer.[/COLOR]


[COLOR=#000000]Unpacking JRE (Java Runtime Environment) ...[/COLOR]
[COLOR=#000000]Unzipping JRE ...[/COLOR]
**[COLOR=#000000]cdinstall.sh: 403: cdinstall.sh: /media/sarosh/Data/GTIse/resource/gzip/gzip.linux: Permission denied[/COLOR]**


[COLOR=#000000]Failed to Unzip JRE !![/COLOR]


[COLOR=#000000]Please define GTTEMPDIR env-var to locate a [/COLOR]
[COLOR=#000000]temporary install directory (at least 200MB)[/COLOR]




[COLOR=#000000]Removing [/media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565] ...[/COLOR]


[COLOR=#000000]cdinstall.sh: 418: exit: Illegal number: -1[/COLOR]
```

[COLOR=#000000]What I have tried:[/COLOR]

[COLOR=#000000]1. Sudo and logging in as root using su[/COLOR]
[COLOR=#000000]2. Instead of using the Data partition on my computer I have tried to copy everything to the /home directory and still get the same error. Any Idea what the problem is? [/COLOR]

[COLOR=#000000]I have posted something similar here before but that was continued onto a different initial problem I was having so I made a separate post for this error.

Thanks[/COLOR]

---

### Post by sarosh2 on 2014-03-23
here is the full script file

```
#!/bin/sh

VERSION="v7.3.0"


echo "-----------------------------------------------------------------"
echo ""
echo "If you experience errors while loading shared libraries,"
echo "the -compat-libstdc++* packages must be installed"
echo ""
echo "If you experieince ***Assertion 'c->xlib.lock' failed*** when"
echo "launching the GUI, update the packages listed below."
echo "    SuSE:  xorg-x11-libxcb 7.2-51.2 or later"
echo "    RH  :  libxcb-1.0-4 or later"
echo ""
echo "-----------------------------------------------------------------"




# If GT-SUITE is in debug mode, put LAX in debug too.
if [ "$GTI_DEBUG" = "true" -o "$GTIDEBUG" = "true" ]; then
  LAX_DEBUG=true
  export LAX_DEBUG
fi


# Not supported on SGI/Irix
if [ `uname -s` = "IRIX" -o `uname -s` = "IRIX64" ]; then
  echo "-----------------------------------------------------------------"
  echo ""
  echo "GT-SUITE $VERSION is not supported on SGI/IRIX."
  echo ""
  echo "-----------------------------------------------------------------"
  exit 1
fi


# This script does not support IBM/AIX
if [ `uname -s` = "AIX" ]; then
 echo "-----------------------------------------------------------------"
 echo ""
 echo "GT-SUITE $VERSION is not supported on IBM/AIX."
 echo ""
 echo "-----------------------------------------------------------------"
 exit 1
fi


if [ `uname -m` = "ia64" ]; then
  echo "-----------------------------------------------------------------"
  echo ""
  echo "GT-SUITE $VERSION is not supported on linux_ia64."
  echo ""
  echo "-----------------------------------------------------------------"
  exit 1
fi


# Bug 32732 - Only Linux platform is supported started in 72.
osName=`uname -s 2> /dev/null | tr "[A-Z]" "[a-z]" 2> /dev/null`
case "$osName" in
	*solaris*|*sunos*)
		echo "-----------------------------------------------------------------"
		echo ""
		echo "GT-SUITE $VERSION is not supported on Solaris/SUN."
		echo "As of v7.0 this platform is no longer supported to run the GT-SUITE solver or GUI."
		echo "-To install the license server for this operating system, please see the"
		echo "documentation in the root folder on the CD."
		echo "-To install GT-Link for this operating system (CFD coupling library),"
		echo "please see the "Special instructions for UNIX" section in the CFD coupling tutorial."
		echo "-If this system is your file server and you are trying to install a networked"
		echo "copy for a supported platform, please run the installer from the supported platform."
		echo ""
		echo "-----------------------------------------------------------------"
		exit 1
    ;;
	*hp-ux*|*hpux*)
		echo "-----------------------------------------------------------------"
		echo ""
		echo "GT-SUITE $VERSION is not supported on HP."
		echo "As of v7.0 this platform is no longer supported to run the GT-SUITE solver or GUI."
		echo "-To install the license server for this operating system, please see the"
		echo "documentation in the root folder on the CD."
		echo "-To install GT-Link for this operating system (CFD coupling library),"
		echo "please see the "Special instructions for UNIX" section in the CFD coupling tutorial."
		echo "-If this system is your file server and you are trying to install a networked"
		echo "copy for a supported platform, please run the installer from the supported platform."
		echo ""
		echo "-----------------------------------------------------------------"
		exit 1
    ;;
	*aix*)
		echo "-----------------------------------------------------------------"
		echo ""
		echo "GT-SUITE $VERSION is not supported on IBM/AIX."
		echo "As of v7.0 this platform is no longer supported to run the GT-SUITE solver or GUI."
		echo "-To install the license server for this operating system, please see the"
		echo "documentation in the root folder on the CD."
		echo "-To install GT-Link for this operating system (CFD coupling library),"
		echo "please see the "Special instructions for UNIX" section in the CFD coupling tutorial."
		echo "-If this system is your file server and you are trying to install a networked"
		echo "copy for a supported platform, please run the installer from the supported platform."
		echo ""
		echo "-----------------------------------------------------------------"
		exit 1
    ;;
	*)
    ;;
esac


# Save current directory.
originalPWD=`pwd`


# Ensure the user specified GTTEMPDIR is valid (the directory exist).
if [ $GTTEMPDIR ]; then
  if [ ! -d "$GTTEMPDIR" ]; then
    echo ""
    echo "You have specified GTTEMPDIR=$GTTEMPDIR for temporary JRE unpacking."
    echo "However, [$GTTEMPDIR] does not exist or is not a directory !"
    echo ""
    exit -1
  fi
fi


# If User did not specify any GTTEMPDIR, use /tmp
if [ -z "$GTTEMPDIR" ]; then
  GTTEMPDIR=/tmp
fi


# If GTTEMPDIR is not valid, use $HOME
if [ ! -d "$GTTEMPDIR" ]; then
  echo ""
  echo "WARNING: [$GTTEMPDIR] is not a directory !"
  echo "Using $HOME to extract JRE for installation ..."
  echo ""
  GTTEMPDIR="$HOME"
fi


#################################################################################################
# Bug - 12229 Check space on /tmp and exit install if not enough.
if [ "$GTTEMPDIR" = "/tmp" ]; then
	if [ `uname -s` = "SunOS" ]; then
		DF_CMD='/usr/xpg4/bin/df -P'
	else
		DF_CMD='df -P'
	fi
sePwd=`pwd`
cd "$GTTEMPDIR"
DF_AVAIL_COL=4




# This checks if the -n 1 argument works
[ $LAX_DEBUG ] && echo 'Checking tail options...'
TAIL_CMD='tail -n 1 /dev/null'
if $TAIL_CMD 2>/dev/null
then
	TAILN1ARG="-n 1";
else
	TAILN1ARG="-1";
fi
[ $LAX_DEBUG ] && echo "Using tail $TAILN1ARG."




# Gather disk free-space info
#
[ $LAX_DEBUG ] && echo "Gathering free-space information..."


SPACE_NEEDED="200"


AVAIL_SPACE=`$DF_CMD $GTTEMPDIR 2>/dev/null | awk "{print \\\$$DF_AVAIL_COL}" | tail $TAILN1ARG`


DU_S_CMD=`du -s $GTTEMPDIR 2>/dev/null | awk "{print \\\$1}"`


DU_SK_CMD=`du -sk $GTTEMPDIR 2>/dev/null | awk "{print \\\$1}"`


if [ "$DU_S_CMD" -ge "$DU_SK_CMD" ]; then
	RESULT_VAR=`expr $DU_S_CMD / $DU_SK_CMD`
	AVAIL_SPACE=`expr $AVAIL_SPACE / $RESULT_VAR`
fi
AVAIL_SPACE=`expr $AVAIL_SPACE / 1024`
[ $LAX_DEBUG ] && echo "Available space: $AVAIL_SPACE MB"


echo ""
echo "Available Space(MB): $AVAIL_SPACE    Needed Space(MB): $SPACE_NEEDED"
if [ ! -z $AVAIL_SPACE -o -z $SPACE_NEEDED ]; then
	if [ ${AVAIL_SPACE:-0} -lt ${SPACE_NEEDED:-0} ]; then
	    echo ""
		echo "WARNING! The disk space available is less than the required space (200MB)"
		echo ""
		echo "The temporary directory used during installation [$GTTEMPDIR]"
		echo "does not have enough disk space. A total of [200MB] is required. The"
		echo "installation will exit now. Please set the environment variable GTTEMPDIR to"
		echo "specify a directory with at least this much space and install again."
		echo ""
		exit 1
    fi
else
		echo "WARNING! The amount of disk space required and/or available"
		echo "could not be determined.  The installation will be attempted anyway."
fi
cd $sePwd
fi


#################################################################################################


# Create temporary scratch-pad directory for our installer.
installTempDir="$GTTEMPDIR/gt.install.$$"
echo ""
echo ""
echo "Creating temporary install directory: $installTempDir"
echo ""
echo "To change the temporary directory for the installer, please cancel"
echo "the installer, export GTTEMPDIR=SomeTempDir, and restart the installer."
echo ""
mkdir -p "$installTempDir" > /dev/null 2>&1
if [ $? -ne 0 ]; then
  echo "The temporary install directory"
  echo "        [$GTTEMPDIR]"
  echo "does not exist or you do not have permission to write to it."
  echo "Please set the GTTEMPDIR environment variable to a directory"
  echo "to which you have the permission."
  exit -1
fi


# Create folder to unpack JRE into ...
jreDir="$installTempDir/jre"
mkdir -p "$jreDir" > /dev/null 2>&1


osName=`uname -s 2> /dev/null | tr "[A-Z]" "[a-z]" 2> /dev/null`
case "$osName" in
	*linux*)
    osPlat="linux_x86"
    gzipPlat="linux"
    ;;
	*)
    ;;
esac
if [ -z "$osPlat" ]; then
  echo "---------------------------------------------------------------"
  echo "Could not recognize platform."
  echo "The product is only supported for Linux."
  echo "---------------------------------------------------------------"
  exit -1
fi




# Base directory where the installer is located.
##################################################################################
# resolveLink()
# param		$1					a file or directory name
# sets		$resolveLink		the name of the linked disk entity
##################################################################################


if [ -x /bin/ls ]; then
	lsCMD="/bin/ls"
elif [ -x /usr/bin/ls ]; then
	lsCMD="/usr/bin/ls"
else
	lsCMD="ls"
fi


resolveLink()
{
	rl_linked="true"
	rl_operand="$1"
	rl_origDir="`dirname "$1"`"


	# MMA - 2001.04.04 - if 'dirname' returns '.', then we need
  # the current working directory path
	if [ "$rl_origDir" = "." ]; then
		rl_origDir=`pwd`
	fi


	rl_ls=`$lsCMD -l "$rl_operand"`


	# MMA - 2001.02.28 - always resolve path to absolute.


	while [ "$rl_linked" = "true" ]; do
		# if the operand is not of an abs path, get its abs path
		case "$rl_operand" in
			/*)
				rl_origDir=`dirname "$rl_operand"`
			;;
			\./*)
				rl_origDir=`pwd`
				rl_operand="$rl_origDir/$rl_operand"
			;;
			\../*)
				rl_origDir=`pwd`
				rl_operand="$rl_origDir/$rl_operand"
			;;
			*)
				rl_operand="$rl_origDir/$rl_operand"
			;;
		esac
		#
		# the prevPrev hack is here because .../java often points to .java_wrapper.
		# at the end of the resolution rl_operand actually points to garbage
		# signifying it is done resolving the link.  So prev is actually .java_wrapper.
		# but we want the one just before that, its the real vm starting poiint we want
		#
		rl_prevOperand="$rl_operand"
		rl_ls=`$lsCMD -l "$rl_operand"`
		# get the output ls into a list
		set x $rl_ls
		# get rid of x and file info from ls -l
		shift 9


		#is this a link?
		case "$rl_ls" in
			*"->"*)
				rl_linked="true"
				# is a link, shift past the "->"
				rl_linker=""
				while [ "$1" != "->" -a $# -gt 1 ]; do
					rl_linker="$rl_linker $1"
					shift
				done


				if [ "$1" = "->" ]; then
					shift
				fi
			;;
			*)
				# not a link, the rest must be the targets name
				rl_linked="false"
			;;
		esac
		# now grab what's left
		rl_linkee="$@"


		# debugOut "Following link to LAX $rl_linker -> $rl_linkee"


		if [ "$rl_linked" = "true" -a "`basename "$rl_linkee"`" != "$vmScript" ]; then
			# set to true incase the thing linked to is also a link and we can
			# try again.  The current think linked to now becomes the operand
			rl_operand="$rl_linkee"
			# if the linkee is not abs, make it abs relative to the linker
			case "$rl_operand" in
				/*)
				;;
				*)
					rl_operand="$rl_origDir/$rl_operand"
				;;
			esac
		else
			# otherwise, this operand is not a link itself and we are done
			rl_resolvedLink="$rl_prevOperand"
			# however, do not resolve the last leg of a VMs linked scripts. this will
			# disrupt their scripts.  it is expecting a link to the .java* script
			# let us believe it is not linked and continue on...
			if [ "`basename "$rl_linkee"`" = "$vmScript" ]; then
				rl_linked="false"
			fi
		fi
		# make sure the path returned is absolute
		case "$rl_operand" in
			\.\/*)
				rl_operand="`pwd`/$rl_operand"
			;;
		esac
	done


	# remove "/./" in paths, make it "/"
	# i,e,  "/a/b/./c" becomes "/a/b/c"
	resolvedLink=`echo "$rl_resolvedLink" |  sed 's,/\./,/,'`
}
resolveLink "$0"


absoluteScriptPath="$resolvedLink"
installerDir=`dirname $absoluteScriptPath`
resourceDir="$installerDir/resource"
jreZipName="jre_${osPlat}.tgz"
jreTarName="jre_${osPlat}.tar"
licensingDir="$installerDir/licensing"


if [ "$LAX_DEBUG" = "true" ]; then
  echo jreZipName=$jreZipName
  echo jreTarName=$jreTarName
fi


# Unpack the jre
echo "Unpacking JRE (Java Runtime Environment) ..."
# TODO cant depend on gzip and tar being in user's $PATH
# TODO Is it possible to directly gunzip to destination folder w/o copying...
cp "$resourceDir/jre/$jreZipName" "$jreDir" 1>/dev/null 2>&1
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to copy JRE to $jreDir !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 200MB)"
  echo ""
  # Remove the temporary directory (Bug 6050 Clean up temp files.)
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  #
  exit -1
fi
cd "$jreDir"
GZIP_EXE="$resourceDir/gzip/gzip.${gzipPlat}"
if [ "$LAX_DEBUG" = "true" ]; then
  echo GZIP_EXE=$GZIP_EXE
fi
echo "Unzipping JRE ..."
"$GZIP_EXE" -d "$jreZipName"
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to Unzip JRE !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 200MB)"
  echo ""
  # Remove the temporary directory (Bug 6050 Clean up temp files.)
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  #
  exit -1
fi
echo "Untarring JRE ..."
tar xf "$jreTarName"  # TODO Can we ship gzip and tar utilities with installer !?!
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to Untar JRE !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 200MB)"
  echo ""
  # Remove the temporary directory (Bug 6050 Clean up temp files.)
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  #
  exit -1
fi


##############################################################################
# Done Unpacking JRE - Get on with invoking installer now.
##############################################################################


# Request InstallAnywhere to use the same scratchpad directory.
IATEMPDIR="$installTempDir"
export IATEMPDIR


# Go back to original directory before invoking installer.
cd "$originalPWD"


# ensure DISPLAY env-var is set.
if [ -z "$DISPLAY" ]; then
  echo ""
  echo "---------------------------------------------------------------"
  echo "The environment variable DISPLAY must be set to run the"
  echo "graphical installation program. It has been reset to local"
  echo "machine."
  echo "If a JAVA exception occurs, it may be necessary to run the"
  echo "command 'xhost +' so the program may be displayed."
  echo "---------------------------------------------------------------"
  echo ""
  # set the default value for DISPLAY variable.
  DISPLAY=":0.0"
  export DISPLAY
fi


temp_installdocs="$installTempDir/InstallDocs"
temp_licensing="$installTempDir/licensing"
temp_gzip="$installTempDir/gzip"


mkdir -p "$temp_installdocs" > /dev/null 2>&1
mkdir -p "$temp_gzip" > /dev/null 2>&1
mkdir -p "$temp_licensing" > /dev/null 2>&1


echo ""
echo "[$licensingDir] is being copied to: [$temp_licensing]"


cp "$licensingDir/flm-linux.tar.gz" "$temp_licensing/flm-linux.tar.gz"
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to copy flm-linux.tar.gz !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 200MB)"
  echo ""
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  exit -1
fi


echo "[$licensingDir] was successfully copied to: [$temp_licensing]"
echo ""


cp "$resourceDir/gzip/gzip.linux" "$installTempDir/gzip/gzip.linux"
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to copy gzip.linux !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 800MB)"
  echo ""
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  exit -1
fi


echo "[$installerDir/InstallationNotes.pdf] is being copied to: [$temp_installdocs]"


cp "$installerDir/InstallationNotes.pdf" "$temp_installdocs/InstallationNotes.pdf"
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to copy InstallationNotes.pdf !!"
  echo ""
  echo "Please define GTTEMPDIR env-var to locate a "
  echo "temporary install directory (at least 800MB)"
  echo ""
    cd "$originalPWD"
    echo ""
    echo "Removing [$installTempDir] ..."
    echo ""
    rm -rf "$installTempDir"
  exit -1
fi


echo "[$installerDir/InstallationNotes.pdf] was successfully copied to: [$temp_installdocs]"
echo "====================================================================="
echo ""


installerFolder="GenericUnix"


# Invoke the InstallAnywhere Installer with proper LAX_VM argument
javaExe="$jreDir/bin/java"
installExe="$installerDir/Disk1/InstData/$installerFolder/GTsuite_v730.bin LAX_VM $javaExe $@"
echo "Running $installExe"
$installExe




##############################################################################
# Done Installing. Finish the final cleanup operation ...
##############################################################################


# Remove the temporary directory
cd "$originalPWD"
echo ""
echo "cd-installer is sleeping for 5 seconds ..."
sleep 5
echo ""
echo "Removing [$installTempDir] ..."
echo ""
rm -rf "$installTempDir"


echo "End"


exit 0



```


I have also tried to set the temporary directory in the /home directory still no luck.

---

### Post by sarosh2 on 2014-03-23
[COLOR=#000000]here are the instructions given in the documentation of the software:[/COLOR]

[COLOR=#000000]Linux ONLY - If the CD does not automatically mount, it may be done manually. This may require[/COLOR]
[COLOR=#000000]root privileges and can be done by the following commands or similar, depending on the mount[/COLOR]
[COLOR=#000000]point:[/COLOR]
[COLOR=#000000]mount /dev/cdrom /cdrom[/COLOR]
[COLOR=#000000]8. Linux ONLY - From the terminal window where the installation will be run, set the environment[/COLOR]
[COLOR=#000000]variable GTTEMPDIR to a directory with a minimum of 800 MB of available space. This directory[/COLOR]
[COLOR=#000000]will be used as temporary storage during installation. If this variable is not explicitly set, the[/COLOR]
[COLOR=#000000]installation will default to /tmp. Note that on many systems, the /tmp directory will NOT have[/COLOR]
[COLOR=#000000]enough space and this could cause system stability issues.[/COLOR]
[COLOR=#000000]9. Linux ONLY -Start the installation program from the CD-ROM by calling the script[/COLOR]
[COLOR=#000000]cdinstall.sh. Note it is important that cdinstall.sh is not started from the root directory where[/COLOR]
[COLOR=#000000]it exists. Otherwise it may not be possible to unmount disk 1 ("umount /cdrom") when the installer[/COLOR]
[COLOR=#000000]asks for disk 2. The full path to the script should be given (i.e. run /cdrom/cdinstall.sh and NOT[/COLOR]
[COLOR=#000000]./cdinstall.sh)[/COLOR]

[COLOR=#000000]I was not given a CD so cant use instruction 7. The rest of the instructions are for windows based PC.[/COLOR]

---

### Post by Elfy on 2014-03-23
Thread closed. Please do not post duplicates, it dilutes community effort.

---

### Post by sarosh2 on 2014-03-23
[COLOR=#000000]Just copied the setup directory to '/' using root and run from there I am still getting a permission denied error.[/COLOR]

---

### Post by sarosh2 on 2014-03-23
bump, anyone please?

---

### Post by Toz on 2014-03-23
[I]Please be patient and do not bump your thread within 24 hours of your last post. Our members are from all around the world and connect at differing times. If someone can help, they will.
[/I]

That being said, the error message is:
> Please define GTTEMPDIR env-var to locate a 
temporary install directory (at least 200MB)
...and the instructions say (my bolding):
> 8. Linux ONLY - From the terminal window where the installation will be run, [B]set the environment
variable GTTEMPDIR to a directory with a minimum of 800 MB of available space[/B]. This directory
will be used as temporary storage during installation. If this variable is not explicitly set, the
installation will default to /tmp. Note that on many systems, the /tmp directory will NOT have
enough space and this could cause system stability issues.

What did you set GTTEMPDIR to?

EDIT: Do you have enough free space on your drive?
> I was not given a CD so cant use instruction 7
...what were you given?

---

### Post by sarosh2 on 2014-03-23
> **Toz said:**
> [I]Please be patient and do not bump your thread within 24 hours of your last post. Our members are from all around the world and connect at differing times. If someone can help, they will.
[/I]

That being said, the error message is:

...and the instructions say (my bolding):


What did you set GTTEMPDIR to?



EDIT: Do you have enough free space on your drive?

I have about 150GB available on the DATA drive and out of 15GB home partition I have 2.1 GB available. Both are more than 800mb

...what were you given?
I set GTTEMPDIR to a directory I made called GTTEMPD in the setup folder

I have about 150GB available on the DATA drive and out of 15GB home partition I have 2.1 GB available. Both are more than 800mb

I was given a setup folder.

---

### Post by Toz on 2014-03-23
If you have enough free space in /tmp (program states you need at least 800MB free), try the following command:
```
GTTEMPDIR=/tmp sh /full/path/to/cdinstall.sh
```
...where /full/path/to/ is the full path to your cdinstall file.

---

### Post by sarosh2 on 2014-03-23
I tried using the /tmp dir but still get permission denied error. Restarted the computer thinking that will clear out any files made still did not work.

---

### Post by sarosh2 on 2014-03-23
I am using root aswell I dont know why permission is denied.

---

### Post by Toz on 2014-03-23
Hmmm. Something else is the problem. What does the following command return:
```
ls -l /media/sarosh/Data/GTIse/resource/gzip/
```
I wonder if some of the required executables are not marked as such.

---

### Post by sarosh2 on 2014-03-23
> **Toz said:**
> Hmmm. Something else is the problem. What does the following command return:
```
ls -l /media/sarosh/Data/GTIse/resource/gzip/
```
I wonder if some of the required executables are not marked as such.

that command returns the following:
```
total 52
-rw------- 1 sarosh sarosh 51228 Feb  5  2013 gzip.linux
```

What do you mean marked as such?

thanks for your help btw.

---

### Post by Toz on 2014-03-24
Reading through the script you post in post #2 (specifically the section around the error that you are getting):
```

cd "$jreDir"
GZIP_EXE="$resourceDir/gzip/gzip.${gzipPlat}"
if [ "$LAX_DEBUG" = "true" ]; then
  echo GZIP_EXE=$GZIP_EXE
fi
echo "Unzipping JRE ..."
"$GZIP_EXE" -d "$jreZipName"
if [ $? -ne 0 ]; then
  echo ""
  echo "Failed to Unzip JRE !!"
```
...an attempt is made to unzip the file by running:
```
"$GZIP_EXE" -d "$jreZipName"
```
...where **"$GZIP_EXE"** points to **"$resourceDir/gzip/gzip.${gzipPlat}"** and **${gzipPlat}** = linux (therefore, gzip.linux)

The results of the ls -l command you ran shows that gzip.linux is not marked as executable - which would explain the "Permission denied" error you are getting.

I think this is somehow related to the files that you got - the file permissions were not preserved. To fix this particular issue, you could run:
```
chmod a+x /media/sarosh/Data/GTIse/resource/gzip/gzip.linux
```
...and try the install again.

Note: its possible that there are other permission issues with the distribution files you received. You'll run into them during the setup.

---

### Post by sarosh2 on 2014-03-24
after setting that permission it says this:

cdinstall.sh: 403: cdinstall.sh: /GTIse/resource/gzip/gzip.linux: [B]not found
[/B]
it just doesnt want to install and this was in '/' with root. Running the same chmod a+x command for files in 'DATA' drive still gives 'permission denied' error instead of 'not found'

---

### Post by sarosh2 on 2014-03-24
for Data drive I get this:

cdinstall.sh: 403: cdinstall.sh: /media/sarosh/Data/GTIse/resource/gzip/gzip.linux: [B]Permission denied

[/B]that is after setting gzip.linux as an executable using chmod a+x

---

### Post by steeldriver on 2014-03-24
Is /media/sarosh/Data an external USB drive? if so then it is likely NTFS or FAT formatted and doesn't support *nix file permissions. This will complicate things unnecessarily.

In what format were you given the setup files? if it was a tarball, then I suggest unpacking it again from scratch **in your regular home directory** and doing the install from there

Also DON'T use root (or sudo) until/unless you know that you have to and DON'T use sh to execute the script - just make sure it's executable and then do

```
./cdinstall.sh
```

from the containing directory.

Also you have given no evidence that /tmp doesn't have enough space so keep it simple and DON'T define a temporary directory variable. (The default Ubuntu installation puts /tmp on the root partition afaik so /tmp can use any or all of the free space in / - you can check with **df -h /tmp**)

Remember KISS - keep it simple!

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> Is /media/sarosh/Data an external USB drive? if so then it is likely NTFS or FAT formatted and doesn't support *nix file permissions. This will complicate things unnecessarily.

In what format were you given the setup files? if it was a tarball, then I suggest unpacking it again from scratch **in your regular home directory** and doing the install from there

Also DON'T use root (or sudo) until/unless you know that you have to and DON'T use sh to execute the script - just make sure it's executable and then do

```
./cdinstall.sh
```

from the containing directory.

Also you have given no evidence that /tmp doesn't have enough space so keep it simple and DON'T define a temporary directory variable. (The default Ubuntu installation puts /tmp on the root partition afaik so /tmp can use any or all of the free space in / - you can check with **df -h /tmp**)

Remember KISS - keep it simple!

No the the DATA drive is a partition on the internal HDD of this laptop but it is in FAT32. Saying that I have copied the files to '/' and tried installing it from there still no luck. However after setting chmod a+x to the gzip.linux on '/' I get a '**not found**' error instead of '**permission denied**'. As for the format I was given it was an .iso file. 

when I type just '**./cdinstall.sh**' it gives me a bash error saying '**Permission denied**' so that is why I started using [B]sh cdinstall.sh
[/B]


I have tried using /tmp directory or not defining a GTTEMPDIR at all and I get the same **gzip.linux: Permission Denied **error.

---

### Post by steeldriver on 2014-03-24
COPYING the files if the permissions are already messed up by having been on a FAT partition is not going to fix anything - how and where did you obtain the original files?

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> COPYING the files if the permissions are already messed up by having been on a FAT partition is not going to fix anything - how and where did you obtain the original files?

My friend gave it to me on a USB pendrive and he was given these by our university's design office. Funny thing is he installed it and it worked fine for him but not me ?

---

### Post by steeldriver on 2014-03-24
... as raw files or as a tarball / zip archive?

---

### Post by sarosh2 on 2014-03-24
as a .iso file

---

### Post by steeldriver on 2014-03-24
So how did you mount the iso? Please list the steps you took up to the point where you tried to execute the setup script

---

### Post by sarosh2 on 2014-03-24
first I mounted it on** /media/xGTI** using **mount -o rw,loop** command but it said it can only be mounted as **read only **and also gave me the same **permission denied **error for gzip.linux

So I extracted the .iso file into Data partition and tried from there after using **chmod a+x** and **chmod +x** on gzip.linux, I got a **permission denied **error for gzip.linux 

I did the same for / and tried from there after using **chmod a+x** and **chmod +x** on gzip.linux and got a **not found** error for gzip.linux.

---

### Post by steeldriver on 2014-03-24
Can you go back to the original[COLOR=#000000] directory where you mounted the iso (using the loop option) and try

```
./cdsetup
```

from there WITHOUT setting a temporary dir? If it doesn't work, post the outputs of

```

mount

ls -ld .

ls -l ./resource/gzip 

```
[/COLOR]

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> Can you go back to the original[COLOR=#000000] directory where you mounted the iso (using the loop option) and try

```
./cdsetup
```

from there WITHOUT setting a temporary dir? If it doesn't work, post the outputs of

```

mount

ls -ld .

ls -l ./resource/gzip 

```
[/COLOR]

did you mean **./****cdinstall.sh** instead of **./cdsetup** ?

./cdsetup returns no such file or dir

./cdinstall.sh returns the same **permission denied **error without setting any temp dir.

ls -ld returns:
```
dr-xr-xr-x 1 root root 2048 Mar 23  2013 
```

ls -l returns:
```
total 51-r-xr-xr-x 1 root root 51228 Feb  5  2013 gzip.linux



```

can I just ask what you looking for in these outputs?

---

### Post by steeldriver on 2014-03-24
Please be patient, and PLEASE post the EXACT outputs (error messages) that you get - there are subtle differences between permission denied messages that may indicate whether it is a problem with the **executable **permissions or the **action **it's trying to take (e.g. the permissions on a** target file or directory**)

I am trying to see the PERMISSIONS, OWNERSHIP and MOUNT OPTIONS (for example if the ISO is mounted with 'noexec')

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> Please be patient, and PLEASE post the EXACT outputs (error messages) that you get - there are subtle differences between permission denied messages that may indicate whether it is a problem with the **executable **permissions or the **action **it's trying to take (e.g. the permissions on a** target file or directory**)

I am trying to see the PERMISSIONS, OWNERSHIP and MOUNT OPTIONS (for example if the ISO is mounted with 'noexec')

sure heres the full output to ./cdinstall.sh

```
sarosh@sarosh-K52N:/media/xGTI$ ./cdinstall.sh-----------------------------------------------------------------


If you experience errors while loading shared libraries,
the -compat-libstdc++* packages must be installed


If you experieince ***Assertion 'c->xlib.lock' failed*** when
launching the GUI, update the packages listed below.
    SuSE:  xorg-x11-libxcb 7.2-51.2 or later
    RH  :  libxcb-1.0-4 or later


-----------------------------------------------------------------


Available Space(MB): 1151    Needed Space(MB): 200




Creating temporary install directory: /tmp/gt.install.11388


To change the temporary directory for the installer, please cancel
the installer, export GTTEMPDIR=SomeTempDir, and restart the installer.


Unpacking JRE (Java Runtime Environment) ...
Unzipping JRE ...
./cdinstall.sh: 403: ./cdinstall.sh: /media/xGTI/resource/gzip/gzip.linux: not found


Failed to Unzip JRE !!


Please define GTTEMPDIR env-var to locate a 
temporary install directory (at least 200MB)




Removing [/tmp/gt.install.11388] ...


./cdinstall.sh: 418: exit: Illegal number: -1



```

and for [COLOR=#000000]ls -ld returns:[/COLOR]
[COLOR=#000000]```
[/COLOR][COLOR=#000000]
dr-xr-xr-x 1 root root 2048 Mar 23  2013
[/COLOR][COLOR=#000000]
```

[/COLOR]
[COLOR=#000000]ls -ld resource/gzip/gzip.linux returns:

```
[/COLOR]-r-xr-xr-x 1 root root 51228 Feb  5  2013 resource/gzip/gzip.linux
```

[COLOR=#000000]
ls -l resource/gzip/gzip.linux returns:[/COLOR]
[COLOR=#000000]```

total 51
-r-xr-xr-x 1 root root 51228 Feb  5  2013 gzip.linux[/COLOR]
[COLOR=#000000]
```

thats the full output I have given you. thank you for your help btw :)[/COLOR]

---

### Post by steeldriver on 2014-03-24
Is your system 32 bit or 64 bit? what does

```
file resource/gzip/gzip.linux
```

say?

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> Is your system 32 bit or 64 bit? what does

```
file resource/gzip/gzip.linux
```

say?

I am pretty sure I installed 64-bit ubuntu. here is the output:

```

resource/gzip/gzip.linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

```

---

### Post by steeldriver on 2014-03-24
OK so notice that the error is not "permission denied" but 

```

./cdinstall.sh: 403: ./cdinstall.sh: /media/xGTI/resource/gzip/gzip.linux: **not found**

```

This error sometimes happens when trying to execute a binary file of the wrong architecture (in this case 32 bit binary on a 64 bit system). Since we know the file is there and is marked as executable that seems to be the most likely explanation. It really means that some shared library files that the executable depends on can't be found - you may be able to see exactly which libraries by doing

```
**ldd** /media/xGTI/resource/gzip/gzip.linux
```

Unfortunately it looks like the distributor of the script decided to package their own (32-bit) version of gzip "just in case" the target system didn't have its own version (very unlikely in this day and age) - and then force the installer to use it.

Probably the easiest way forward is to copy the xGTI directory to your home dir (**NOT to a FAT partition** this time) and then edit the script to use the regular 'gzip' instead of "$GZIP_EXE"

However there may be other gotchas if the installer is assuming a 32-bit platform

---

### Post by sarosh2 on 2014-03-24
> **steeldriver said:**
> OK so notice that the error is not "permission denied" but 

```

./cdinstall.sh: 403: ./cdinstall.sh: /media/xGTI/resource/gzip/gzip.linux: **not found**

```

This error sometimes happens when trying to execute a binary file of the wrong architecture (in this case 32 bit binary on a 64 bit system). Since we know the file is there and is marked as executable that seems to be the most likely explanation. It really means that some shared library files that the executable depends on can't be found - you may be able to see exactly which libraries by doing

```
**ldd** /media/xGTI/resource/gzip/gzip.linux
```

Unfortunately it looks like the distributor of the script decided to package their own (32-bit) version of gzip "just in case" the target system didn't have its own version (very unlikely in this day and age) - and then force the installer to use it.

Probably the easiest way forward is to copy the xGTI directory to your home dir (**NOT to a FAT partition** this time) and then edit the script to use the regular 'gzip' instead of "$GZIP_EXE"

However there may be other gotchas if the installer is assuming a 32-bit platform

ok so how do I edit the script to use gzip ? should I just replace $GZIP_EXE with GZIP ? I am sorry I am still new trying to learn so I wouldnt know how to do that.

---

### Post by steeldriver on 2014-03-24
Try changing line 440 of the script

```

cd "$jreDir"
[COLOR=#ff0000]GZIP_EXE="$resourceDir/gzip/gzip.${gzipPlat}"
[/COLOR]if [ "$LAX_DEBUG" = "true" ]; then
  echo GZIP_EXE=$GZIP_EXE
fi
echo "Unzipping JRE ..."

```

to 

```

cd "$jreDir"
[COLOR=#0000ff]GZIP_EXE="/bin/gzip"
[/COLOR]if [ "$LAX_DEBUG" = "true" ]; then
  echo GZIP_EXE=$GZIP_EXE
fi
echo "Unzipping JRE ..."

```

---

