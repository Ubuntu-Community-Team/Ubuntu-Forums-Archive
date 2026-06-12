---
title: "How do I set environment variables for .sh installation file?"
date: 2014-03-22
forum: General Help
---

### Post by sarosh2 on 2014-03-22
Hello, I am trying to install a software called GTSuite. The instructions say I need to set an environment variable called GTTEMPDIR as some temporary directory. I dont know how to do this, can anyone help me? 

I use the command sudo sh ./cdinstall.sh to execute the file.

Full installation instructions are:
Linux ONLY - From the terminal window where the installation will be run, set the environment
variable GTTEMPDIR to a directory with a minimum of 800 MB of available space. This directory
will be used as temporary storage during installation. If this variable is not explicitly set, the
installation will default to /tmp. Note that on many systems, the /tmp directory will NOT have
enough space and this could cause system stability issues.

it tends to otherwise use /TMP which does not seem to have enough memory for some reason ?

I believe two ways of going about it either I can increase the /TMP size somehow or set the environment variable GTTEMPDIR to a temporary directory of my choice?

What should I do?

Thank you.

---

### Post by Lars Noodén on 2014-03-22
You can see which partitions have enough space using [df](http://manpages.ubuntu.com/manpages/saucy/en/man1/df.1.html)

```

df -h

```

Then you should be able to set the variable in the command line.  Here it would be /tmp

```

sudo GTTEMPDIR=/tmp/ sh ./cdinstall.sh

```

but depending on your setup it could be something else with more space.  Filling up /tmp or /var/tmp causes problems on live systems.

---

### Post by sarosh2 on 2014-03-22
I dont get it now its giving me this error:

Creating temporary install directory: /media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565


To change the temporary directory for the installer, please cancel
the installer, export GTTEMPDIR=SomeTempDir, and restart the installer.


Unpacking JRE (Java Runtime Environment) ...
Unzipping JRE ...
cdinstall.sh: 403: cdinstall.sh: /media/sarosh/Data/GTIse/resource/gzip/gzip.linux: Permission denied


Failed to Unzip JRE !!


Please define GTTEMPDIR env-var to locate a 
temporary install directory (at least 200MB)




Removing [/media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565] ...


cdinstall.sh: 418: exit: Illegal number: -1

why is permission denied ? I have tried with sudo and su

---

### Post by sarosh2 on 2014-03-22
GTTEMPD is the temporary directory I wish to use and it is on second local hard drive partition called DATA.

---

### Post by sarosh2 on 2014-03-22
I tried copy the GTIse setup folder to /home and running it from there it still says permission denied for gzip.linux. Any help will be greatly appreciated. Thank you.

---

### Post by Lars Noodén on 2014-03-22
Which site did you get the script from?

---

### Post by sarosh2 on 2014-03-22
My friend gave it to me who got it from the University as they dont give out CDs. its the weekend and I need to get this running so cant even seek help from the helpdesk.

---

### Post by Lars Noodén on 2014-03-22
What is the exact line you are typing that gives you the error?  Also what is the output of *df -h*, to see where there is space?

---

### Post by sarosh2 on 2014-03-22
output of dh -f:

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        15G   8.3G  5.3G  62% /
none        4.0K       0  4.0K   0% /sys/fs/cgroup
udev        1.4G   4.0K  1.4G   1% /dev
tmpfs       276M  1.3M  275M   1% /run
none        5.0M         0  5.0M   0% /run/lock
none        1.4G    484K  1.4G   1% /run/shm
none        100M     64K  100M   1% /run/user
/dev/sda5       188G     44G  144G  24% /media/sarosh/Data

the exact line I am typing is:

GTTEMPDIR=/media/sarosh/Data/GTIse/GTTEMPD sh cdinstall.sh


or

GTTEMPDIR=/media/sarosh/Data/GTIse/GTTEMPD sh ./cdinstall.sh



same thing for /home directory 

any idea whats wrong ?

---

### Post by Lars Noodén on 2014-03-22
If it needed sudo then you need to add that.  If it is to run as a regular user but you previously ran it using sudo, then there might be some files in the way left over from earlier tries.

---

### Post by sarosh2 on 2014-03-22
no that I have tried both with sudo so:

sudo GTTEMPDIR=/media/sarosh/Data/GTIse/GTTEMPD sh cdinstall.sh

and then logged in as root and typed just

GTTEMPDIR=/media/sarosh/Data/GTIse/GTTEMPD sh cdinstall.sh

if there are files left anyway how do I clean them?

---

### Post by sarosh2 on 2014-03-22
I have tried searching for how to find left over files, I am not really sure what to look for....

---

### Post by Lars Noodén on 2014-03-22
Unfortunately it would depend on where the script makes them.  Can you paste the error messages? Maybe someone here can spot something.

---

### Post by Lars Noodén on 2014-03-22
Also, what do the installation instructions say to do?  Usually there is a file labelled README or INSTALL or something like that that accompanies the other stuff.

---

### Post by sarosh2 on 2014-03-22
I have followed the instructions, there are only two anyway. One of them says to make the GTTEMPDIR which I have done already. I will post the second instruction and the full script file once I get home.

Here is the error I am getting after executing the script file cdinstall.sh after defining a GETTEMPDIR:

[COLOR=#000000]Creating temporary install directory: /media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565[/COLOR]


[COLOR=#000000]To change the temporary directory for the installer, please cancel[/COLOR]
[COLOR=#000000]the installer, export GTTEMPDIR=SomeTempDir, and restart the installer.[/COLOR]


[COLOR=#000000]Unpacking JRE (Java Runtime Environment) ...[/COLOR]
[COLOR=#000000]Unzipping JRE ...[/COLOR]
[COLOR=#000000]cdinstall.sh: 403: cdinstall.sh: /media/sarosh/Data/GTIse/resource/gzip/gzip.linux: Permission denied[/COLOR]


[COLOR=#000000]Failed to Unzip JRE !![/COLOR]


[COLOR=#000000]Please define GTTEMPDIR env-var to locate a [/COLOR]
[COLOR=#000000]temporary install directory (at least 200MB)[/COLOR]




[COLOR=#000000]Removing [/media/sarosh/Data/GTIse/GTTEMPD/gt.install.9565] ...[/COLOR]


[COLOR=#000000]cdinstall.sh: 418: exit: Illegal number: -1








[/COLOR]

---

### Post by Lars Noodén on 2014-03-22
Which filesystem does /media/sarosh/Data/ use?

---

### Post by sarosh2 on 2014-03-22
its **fat32 **and here are the instructions

Linux ONLY - If the CD does not automatically mount, it may be done manually. This may require
root privileges and can be done by the following commands or similar, depending on the mount
point:
mount /dev/cdrom /cdrom
8. Linux ONLY - From the terminal window where the installation will be run, set the environment
variable GTTEMPDIR to a directory with a minimum of 800 MB of available space. This directory
will be used as temporary storage during installation. If this variable is not explicitly set, the
installation will default to /tmp. Note that on many systems, the /tmp directory will NOT have
enough space and this could cause system stability issues.
9. Linux ONLY -Start the installation program from the CD-ROM by calling the script
cdinstall.sh. Note it is important that cdinstall.sh is not started from the root directory where
it exists. Otherwise it may not be possible to unmount disk 1 ("umount /cdrom") when the installer
asks for disk 2. The full path to the script should be given (i.e. run /cdrom/cdinstall.sh and NOT
./cdinstall.sh)

As you know I am not given a CD so cant use instruction 7. The rest of the instructions are for windows based PC.

---

### Post by sarosh2 on 2014-03-22
Here is the script file:
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
thanks for your help :)

---

### Post by sarosh2 on 2014-03-22
As for the filesystem of DATA drive. I have tried installing it on the linux home partition too and it still doesnt work. I get the same error saying permission denied on gzip.linux

---

### Post by sarosh2 on 2014-03-23
bump

---

### Post by efflandt on 2014-03-23
Didn't notice multiple pages already discussing what I was going to suggest. Although, now that I look back, nobody had suggested using default /tmp if it requires 800 MB (or 200 MB) and / has 5.3 MB available.

---

### Post by sarosh2 on 2014-03-23
The permissions for "me" are create and delete files. I am just changing the "group" and "other" permissions to see what happens. saying that I have tried it on the linux ext partition in /home too but still no joy. I am not sure about the /tmp the script seems to think there isnt enough space on it for some reason. I will post the error from using /tmp too.

---

### Post by sarosh2 on 2014-03-23
```
Available Space(MB): 5337    Needed Space(MB): 200



Creating temporary install directory: /tmp/gt.install.17446


To change the temporary directory for the installer, please cancel
the installer, export GTTEMPDIR=SomeTempDir, and restart the installer.


Unpacking JRE (Java Runtime Environment) ...
Unzipping JRE ...
cdinstall.sh: 403: cdinstall.sh: /media/sarosh/Data/GTIse/resource/gzip/gzip.linux: Permission denied


Failed to Unzip JRE !!


Please define GTTEMPDIR env-var to locate a 
temporary install directory (at least 200MB)




Removing [/tmp/gt.install.17446] ...


cdinstall.sh: 418: exit: Illegal number: -1



```

same issue using /tmp, permission denied on that too ?!

---

### Post by sarosh2 on 2014-03-23
changed the permissions for "group" and "others" for the whole of DATA partition still not working. It wont let me change permissions individually for folders but "me" still has full create and delete rights.

---

### Post by sarosh2 on 2014-03-23
Just copied the setup directory to '/' using root and run from there I am still getting a permission denied error.

---

### Post by Elfy on 2014-03-23
Closed.

[http://ubuntuforums.org/showthread.php?t=2212827](http://ubuntuforums.org/showthread.php?t=2212827)

---

