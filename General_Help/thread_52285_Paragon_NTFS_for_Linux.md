---
title: "Paragon NTFS for Linux"
date: 2005-07-27
forum: General Help
---

### Post by rjpa on 2005-07-27
Hi,

I try to install **Paragon's NTFS for Linux**. I've installed the packages below:

[B]linux-headers
linux-sources
linux-kernel (or something like it)[/B]

... but everytime I try to launch the installer:

```
# sudo sh /tmp/paragon/install.sh
```

I get this error:

```
Can't find the kernel sources. Please, install them and run this program.
```

The install.sh file look like this:
```
#!/bin/sh

if [ `whoami` != root ]; then
    /bin/echo "sorry - you need to be root to install the module"
    exit 1
fi

usage ()
{
    /bin/echo >&2 "Usage: `basename $0` [--interactive] [--iocharset=<charset>]"
    /bin/echo >&2 "          [--help]"
    exit 1
}

AUTO=yes   
TESTONLY=no
IOCHARSET=default

if [ -f /etc/sysconfig/i18n ]; then
  . /etc/sysconfig/i18n
fi

#if [ -n "$SYSFONTACM" ]; then
#    IOCHARSET=$SYSFONTACM
#fi

#for PARM in $*
#do
#    case $PARM in
while [ $# -gt 0 ] ; do
    case $1 in
	-i | --interactive*)
	    AUTO=no
	    shift
	    ;;
	--test*)
	    TESTONLY=yes
	    shift
	    ;;
	--iocharset=*)
	    #IOCHARSET=`/bin/echo "$1" | sed -e 's/^[^=]*=//g'`
	    #IOCHARSET=`/bin/echo "$1" | sed -e "s;--[^=]*=;;"`
            IOCHARSET=`/bin/echo "$1" | sed 's/^--iocharset=//'`
	    shift
	    ;;
	-c)
#	    if [ $# -lt 2 ] ; then
#		usage;
#	    else
#		temp="$2"
#	    fi
#	    if [ "$CHARSIZE" = "" -a "${1#-}" -gt 0 -a "${1#-}" -lt 32 ] 2>/dev/null; then
#		CHARSIZE="--char-height ${1#-}"
#		shift
#	    else
#		usage
#	    fi
	    shift
	    if test $# -gt 0; then
	    	IOCHARSET=$1 # in realuty it is $2 
		shift
	    else
	    	/bin/echo "no charset specified"
		usage
		exit 1
	    fi
	    ;;
	-h | -? | --help*)
	    shift
	    usage
	    exit 0
	    ;;
	*)
	    shift
	    /bin/echo "$0: unknown option $1"
	    usage
	    exit 1
	    ;;
    esac
done

if [ -e /usr/src/linux ]; then
    KERNELPATH=/usr/src/linux
else
    if [ -e /usr/src/Linux ]; then
	KERNELPATH=/usr/src/Linux
    else
	if [ -e /usr/src/linux-`uname -r` ]; then
	    KERNELPATH=/usr/src/linux-`uname -r`
	else
	    if [ -e /usr/lib/kernel/linux ]; then
		KERNELPATH=/usr/lib/kernel/linux
	    else
		if [ -e /usr/lib/kernel/linux-`uname -r` ]; then
		    KERNELPATH=/usr/lib/kernel/linux-`uname -r`
		else
		    /bin/echo "Can't find the kernel sources. Please, install them and run this program."
		    exit 1
		fi	
	    fi
	fi
    fi		
fi

if [ ! -h /usr/include/linux ]; then
    if [ -d /usr/include/linux ]; then
	if [[ "$AUTO" = "no" ]]; then
	    /bin/echo "Directory /usr/include/linux exists. Create symlink to real kernel headers? [yes/no]"
	    read answer
	    case "$answer" in
		y|Y|yes|Yes|YES)
		    /bin/echo "Directory /usr/include/linux will be saved as /usr/include/linux.default"
		    mv /usr/include/linux /usr/include/linux.default
		    ;;
		*)
		    /bin/echo "Umpossibly to continue installation. Program will be terminated."
		    exit 1
		    ;;
	    esac
	else
	    mv /usr/include/linux /usr/include/linux.default
	fi
    fi
    [ $TESTONLY = "no" ] && ln -s $KERNELPATH/include/linux /usr/include/linux
fi

if [ ! -h /usr/include/asm ]; then
    if [ -d /usr/include/asm ]; then
	if [[ "$AUTO" = "no" ]]; then
	    /bin/echo "Directory /usr/include/asm exists. Create symlink to real kernel headers? [yes/no]"
	    read answer
	    case "$answer" in
		y|Y|yes|Yes|YES)
		    /bin/echo "Directory /usr/include/asm will be saved as /usr/include/asm.default"
		    mv /usr/include/asm /usr/include/asm.default
		    ;;
		*)
		    /bin/echo "Umpossibly to continue installation. Program will be terminated."
		    exit 1
		    ;;
	    esac
	else
	    mv /usr/include/asm /usr/include/asm.default
	fi
    fi
    [ $TESTONLY = "no" ] && ln -s $KERNELPATH/include/asm /usr/include/asm
fi

if [ ! -x "`which gcc 2>/dev/null`" -o ! -x "`which make 2>/dev/null`" ]; then
    /bin/echo "Can't find make or gcc. Program can't work any longer"
    exit 1
fi

cd ./ifslinux
# set current VERSION, PATCHLEVEL, SUBLEVEL, EXTRAVERSION
eval `sed -n -e 's/^\([A-Z]*\) = \([0-9]*\)$/\1=\2/p' -e 's/^\([A-Z]*\) = \(-[-a-z0-9]*\)$/\1=\2/p' $KERNELPATH/Makefile`
if [ -z "$VERSION" -o -z "$PATCHLEVEL" -o -z "$SUBLEVEL" ]
then
    /bin/echo "unable to determine current kernel version" >&2
    exit 1
fi

#KERNELVERSION=$VERSION.$PATCHLEVEL.$SUBLEVEL${EXTRAVERSION}
KERNELVERSION=`sed -n 's/^.define UTS_RELEASE "\(.*\).*"/\1/p' $KERNELPATH/include/linux/version.h`

maked=no

for ver in $KERNELVERSION
do
    MODPATH=/lib/modules/$ver/kernel/
    if [ -d $MODPATH ]; then
        /bin/echo "ufsd driver can be compiled for kernel $ver($VERSION.$PATCHLEVEL.$SUBLEVEL)"
        make clean  >/dev/null 2>&1
	if [ "$VERSION" == "2" ]; then
	    if [ "$PATCHLEVEL" == "4" ]; then
		    /bin/echo "We can build module only for 2.4.x kernels"
		    /bin/cp -f ./objfre/libufsd.a.24 ./objfre/libufsd.a
	    else
		if [ "$PATCHLEVEL" == "5" -o "$PATCHLEVEL" == "6" ]; then
		    /bin/echo "We can build module only for 2.6.x kernels"
		    /bin/cp -f ./objfre/libufsd.a.26 ./objfre/libufsd.a
		else
		    /bin/echo "We can build module only for 2.4.x and 2.6.x kernels"
		fi
	    fi
	else
	    /bin/echo "We can build module only for 2.4.x and 2.6.x kernels"
	    exit 1
	fi
        make  >/dev/null 2>&1

        exitCode=$?
        case $exitCode in
	    0)
		maked=yes
	        ;;
	    *)
	        /bin/echo "Ufsd module was't made"
	        cd ../
	        exit 1
        esac

        CURRKERNEL=`uname -r`

        if [ "$CURRKERNEL" != "$ver" ]; then
	    /bin/echo "Ufsd module was build and will be installed for kernel $ver but current kernel in $CURRKERNEL."
	    if [[ "$AUTO" = "no" ]]; then
	        /bin/echo "Do you want to install module and service?"
	        read answer
	        case "$answer" in
		    y|Y|yes|Yes|YES)
		        /bin/echo "Ok. Trying to install."
		        ;;
		    *)
		        /bin/echo "Program terminated."
		        cd ../
		        exit 1
		        ;;
	        esac
	    fi
        fi

        INSTPATH=/lib/modules/$ver/kernel/fs/ufsd
        if [ -f "$INSTPATH/ufsd.o" ]; then
    	    /bin/rm "$INSTPATH/ufsd.o"
        fi
        if [ -f "$INSTPATH/ufsd.ko" ]; then
    	    /bin/rm "$INSTPATH/ufsd.ko"
        fi

        if [ ! -d $INSTPATH ]; then
	    /bin/echo Creating the directory for module
            /bin/mkdir $INSTPATH
        fi 						
        /bin/echo "Moving module in destination directory..."
	if [ "$PATCHLEVEL" == "4" ]; then
    		    [ $TESTONLY = "no" ] && /bin/cp ./objfre/ufsd.o $INSTPATH
	else
	    if [ "$PATCHLEVEL" == "5" -o "$PATCHLEVEL" == "6" ]; then
		if [ -f ./objfre/ufsd.ko ]; then
    		    [ $TESTONLY = "no" ] && /bin/cp ./objfre/ufsd.ko $INSTPATH
		else
    		    [ $TESTONLY = "no" ] && /bin/cp ./objfre/ufsd.o $INSTPATH/ufsd.ko
		fi
	    fi
	fi
    else
	/bin/echo "Can't find compiled modules for kernel $ver"
    fi 						
done

cd ../

if [[ "$maked" = "no" ]]; then
    /bin/echo "Can't find compiled modules for kernel. Please, compile your kernel and run this program again."
    exit 1
fi

/bin/echo "Finding module dependencies..."
/sbin/depmod >/dev/null 2>&1

szOSType="unknown"

if [[ "$AUTO" = "no" ]]; then
    # Ask the user for linux type.
    /bin/echo >&2 "	`echo -en "\\033[1;36m"` Please select a linux type.`echo -en "\\033[0;39m"`"

    lin_type=
    select lin_type in	\
	    "`echo -e "\\033[1;36m"`RedHat`echo -e "\\033[0;39m"`" 		\
	    "`echo -e "\\033[1;36m"`Mandrake`echo -e "\\033[0;39m"`" 		\
	    "`echo -e "\\033[1;36m"`SuSE`echo -e "\\033[0;39m"`"		\
	    "`echo -e "\\033[1;36m"`Slackware`echo -e "\\033[0;39m"`"		\
	    "`echo -e "\\033[1;36m"`Debian`echo -e "\\033[0;39m"`"		\
	    "`echo -e "\\033[1;36m"`Another linux`echo -e "\\033[0;39m"`"	\
	    "`echo -e "\\033[1;36m"`Skip and continue`echo -e "\\033[0;39m"` - I don't know my linux type."
    do
	case $lin_type in
	    '')
		/bin/echo >&2 'Please enter a number in range.'
		;;
	    ?*)
		case $lin_type in
		    *Skip*)
			szOSType=unknown
		        break
			;;
		    *Another*)
			/bin/echo -n "Please write your Linux name: "
			read othername
			/bin/echo
			szOSType=unknown
		        break
			;;
		    *RedHat*)
			szOSType=redhat
		        break
			;;
		    *Mandrake*)
			szOSType=redhat
		        break
			;;
		    *SuSE*)
			szOSType=SuSE
		        break
			;;
		    *slackware*)
			szOSType=slackware
		        break
			;;
		    *Debian*)
			szOSType=debian
		        break
			;;
		    *)
#		    *' '*)
#			lin_type=$(expr "$lin_type" : '\([^ ]*\)')
#			esac
		        break
		        ;;
		esac
	esac
    done

    case $lin_type in
	'')
	    exit 1;;
	none)
	    ;;
	*)
	    #/bin/echo "$lin_type"
	    ;;
    esac
fi

if [[ "$szOSType" = "unknown" ]]; then
    if [ -x "/sbin/SuSEconfig" ]; then
	if [ -x "`which yast 2>/dev/null`" -o -x "`which yast2 2>/dev/null`" ]; then
	    if [ -e "/sbin/init.d" ]; then
		    /bin/echo "I think you are using a SuSE-like (less 7.1) system"
		    szOSType="SuSE70"
	    else
		if [ -e "/etc/init.d" ]; then
		    /bin/echo "I think you are using a SuSE-like (7.1 or upper) system"
		    szOSType="SuSE71"
		else  
		    /bin/echo "I think you are using a SuSE-like system"
		    szOSType="SuSE"
		fi
	    fi
	fi	    
    else
	if [ -x "`which chkconfig 2>/dev/null`" ]; then
	    if [ -e "/etc/rc.d/init.d" ]; then
		/bin/echo "I think you are using a Redhat-like system"
		szOSType="redhat"
	    else
    		/bin/echo "I can't recognize your operating system and install services"
	        exit 1
	    fi
	else
	    if [ -x "`which dpkg 2>/dev/null`" ]; then
		if [ -e "/etc/init.d" ]; then
		    /bin/echo "I think you are using a Debian-like system"
		    szOSType="debian"
		fi
	    else
		if [ -e "/etc/rc.d/rc.M" ]; then
		    /bin/echo "I think you are using a slackware-like system"
		    szOSType="slackware"
		else
		    /bin/echo "I can't recognize your operating system and install services to load ufsd module at start"
		    /bin/echo "You must load ufsd driver manually"
		    exit 1
		fi
	    fi
	fi
    fi	
fi

if [ $szOSType = "redhat" ]; then
    /bin/echo "Adding services for RedHat like system"
    if [ $TESTONLY = "no" ]; then
	if [ -e "$servicepath/ufsd" ]; then
	    chkconfig --del ufsd
	    /bin/rm -f /etc/rc.d/init.d/ufsd
	fi
	/bin/cp ./init.d/ufsd.rh7 /etc/rc.d/init.d/ufsd
	chkconfig --add ufsd
	if [ ! "$?" -eq 0 ]; then
    	    /bin/echo
    	    /bin/echo "Can't add services"
    	    /bin/echo
	    exit 1
	fi
    fi
fi

# for "SuSE70" "SuSE71" "SuSE"
if [ $szOSType = "SuSE70" -o $szOSType = "SuSE71" -o $szOSType = "SuSE" ]; then
    if [ $szOSType = "SuSE71" ]; then
	servicepath="/etc/init.d"
    else
	servicepath="/sbin/init.d"
    fi
    /bin/echo "Adding services for SuSE like system"
    if [ -x "`which chkconfig 2>/dev/null`" ]; then
	if [ $TESTONLY = "no" ]; then
	    if [ -e "$servicepath/ufsd" ]; then
		chkconfig --del ufsd
		/bin/rm -f $servicepath/ufsd
	    fi
	    /bin/cp ./init.d/ufsd.suse $servicepath/ufsd
	    chkconfig --add ufsd
	    if [ ! "$?" -eq 0 ]; then
    		/bin/echo
    		/bin/echo "Can't add services"
    	        /bin/echo
	        exit 1
	    fi
	fi    
    else
	if [ $TESTONLY = "no" ]; then
	    /bin/cp ./init.d/ufsd.suse $servicepath/ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc2.d/K14ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc2.d/S08ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc3.d/K14ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc3.d/S08ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc5.d/K14ufsd
	    /bin/ln -s $servicepath/ufsd $servicepath/rc5.d/S08ufsd
	fi 
    fi
fi

insmod ufsd >/dev/null 2>&1

cd ./util
make clean >/dev/null 2>&1
make >/dev/null 2>&1

exitCode=$?
case $exitCode in
    0)
	/bin/echo "Utilite was made"
	;;
    *)
	/bin/echo "Utilite was't made"
	cd ../
	exit 1
esac

cd ../

if [ $IOCHARSET != "default" ]; then
    /bin/echo "All ntfs partition will be mounted with iocharset=$IOCHARSET"
fi

ChangeFstab()
{
    if [ -e "./util/parttype" ]; then
	mntletter=0
	for mntdev in `/bin/awk '{print $4}' /proc/partitions` ; do
	    #major minor blocks device
	    type=`./util/parttype "/dev/$mntdev"`
	    if [ "$type" = "ntfs" ]; then
    		/bin/echo "Found NTFS partition /dev/$mntdev "
	        a=$[mntletter++]
		/bin/mkdir -p $1/ntfs_$a
		if [ $IOCHARSET = "default" ]; then
	    	    /bin/cat >> /etc/fstab <<EOF
/dev/$mntdev $1/ntfs_$a ufsd defaults 0 0
EOF
		else
	    	    /bin/cat >> /etc/fstab <<EOF
/dev/$mntdev $1/ntfs_$a ufsd defaults,iocharset=$IOCHARSET 0 0
EOF
		fi
		if ! /bin/grep -iq $1/ntfs_$a /proc/mounts >/dev/null 2>&1 ; then
		    if [ $IOCHARSET = "default" ]; then
			/bin/mount -t ufsd /dev/$mntdev $1/ntfs_$a
		    else
			/bin/mount -t ufsd /dev/$mntdev $1/ntfs_$a -o iocharset=$IOCHARSET
		    fi
    		    /bin/echo "NTFS partition /dev/$mntdev mounted to $1/ntfs_$a"
		fi
	    fi
        done
	if [ $mntletter == "0" ]; then
	    for i in /dev/hd*; do
		type=`./util/parttype "$i"`
		if [ "$type" = "ntfs" ]; then
    		    /bin/echo "Found NTFS partition $i"
	            a=$[mntletter++]
		    /bin/mkdir -p $1/ntfs_$a
		    if [ $IOCHARSET = "default" ]; then
	    	        /bin/cat >> /etc/fstab <<EOF
$i $1/ntfs_$a ufsd defaults 0 0
EOF
		    else
	    	        /bin/cat >> /etc/fstab <<EOF
$i $1/ntfs_$a ufsd defaults,iocharset=$IOCHARSET 0 0
EOF
		    fi
		    if ! /bin/grep -iq $1/ntfs_$a /proc/mounts >/dev/null 2>&1 ; then
		        if [ $IOCHARSET = "default" ]; then
			    /bin/mount -t ufsd $i $1/ntfs_$a
		        else
		    	    /bin/mount -t ufsd $i $1/ntfs_$a -o iocharset=$IOCHARSET
		        fi
    		        /bin/echo "NTFS partition $i mounted to $1/ntfs_$a"
		    fi
		fi	
	    done
	fi
    fi
}    

if [[ "$AUTO" = "no" ]]; then
    /bin/echo "Would you like to mount your NTFS partition at start? [yes/no]"
    read answer
    case "$answer" in
	y|Y|yes|Yes|YES)
	    ChangeFstab /mnt
	    ;;
	*)
	    ;;
    esac
else
    ChangeFstab /mnt
fi
```


What can be wrong?

Cheers
Rasmus

---

### Post by MrCheese on 2005-07-27
open a root terminal (use the sudo password unless you really have set up root, have a look at /usr/src/linux & see if the kernel sources are in there. Normally "linux" is a symlink pointing to the real source tree eg. linux-2.6.10. If this looks alright, try doing "make xconfig" & see if the graphical config dialog comes up which should at least indicate that everything is where it should be. Don't save any changes if prompted!!

Hope this helps,

Mr. Cheese.

---

### Post by rjpa on 2005-07-27
[QUOTE=MrCheese]open a root terminal (use the sudo password unless you really have set up root, have a look at /usr/src/linux & see if the kernel sources are in there. Normally "linux" is a symlink pointing to the real source tree eg. linux-2.6.10. If this looks alright, try doing "make xconfig" & see if the graphical config dialog comes up which should at least indicate that everything is where it should be. Don't save any changes if prompted!!

Hope this helps,

Mr. Cheese.[/QUOTE]

OK,

I get this error now:
```
ufsd driver can be compiled for kernel 2.6.10-5-686(2.6.10)
We can build module only for 2.6.x kernels
Ufsd module was't made
```

When I try to execute: **make xconfig**, I get this error:
```
make: *** No rule to make target `xconfig'.  Stop.
```

What about that??

Cheers
Rasmus

---

### Post by shakin on 2005-07-27
Why not try CaptiveNTFS? I didn't have these problems with Captive.

---

### Post by rjpa on 2005-07-27
[QUOTE=shakin]Why not try CaptiveNTFS? I didn't have these problems with Captive.[/QUOTE]

Hmm, well never got it working :( And I've heard that it was dog slow compared to the Paragon product.

Cheers
Rasmus

---

### Post by AdmiralSenn on 2005-07-29
I haven't gotten Captive working either, and I keep getting advised against it.

I thought there was at least one or two ways to do ntfs read/write from linux safely. Every option I find contradicts that, though.

---

### Post by drigloi on 2005-09-10
Here's the HOWTO:

You basically need to set up kernel headers matching your current kernel. I did this on Hoary with the default kernel (2.6.10-5-386).

Problem is that install.sh expects things in some slightly different locations:

1. It searches kernel headers under /usr/src/linux-`uname -r` (linux-2.6.10-5-386) while Hoary stores these under /usr/src/linux-headers-`uname -r` (linux-headers-2.6.10-5-386 actually)
SOLUTION for this: create a "/usr/src/linux" symlink to /usr/src/linux-headers-2.6.10-5-386
```
sudo ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux
```

2. It searches for kernel modules under /lib/modules/2.6.10 instead of Hoary's /lib/modules/2.6.10-5-386.
SOLUTION: create a "2.6.10" symlink to /lib/modules/2.6.10-5-386 
```
sudo ln -s /lib/modules/2.6.10-5-386 /lib/modules/2.6.10
```

3. The script uses awk and expects it under /bin while Ubuntu has awk under /usr/bin
SOLUTION as you might found out by now: create "awk" symlink under /bin 
```
sudo ln -s /usr/bin/awk /bin/awk
```

Now you'll be able to run install.sh successfully. You also need to mount the NTFS partition with iocharset=utf8 to handle non-US filenames correctly.

NOTE: according to a recent PC Mag's review of Paragon NTFS ([http://madpenguin.org/cms/?m=show&id=5081](http://madpenguin.org/cms/?m=show&id=5081) ) this is a very good tool for writing NTFS under Linux. Too bad it is a proprietary product - but you can download a trial from Paragon's website.

---

### Post by Jipsu on 2005-09-24
I did all mentioned above, of course changed the paths for my kernel..
But I'm still getting message:

ufsd driver can be compiled for kernel 2.6.12-9-amd64-generic(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was't made

Any solutions?

---

### Post by GTvulse on 2005-09-24
[QUOTE=Jipsu]I did all mentioned above, of course changed the paths for my kernel..
But I'm still getting message:

ufsd driver can be compiled for kernel 2.6.12-9-amd64-generic(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was't made

Any solutions?[/QUOTE]
 You cannot mix and match i386 object code with amd64 object code.

As Paragon apparently doesn't supply amd64 binaries of its product, you are out of luck. If you can install Ubuntu i386 in your Athlon 64 box, Paragon NTFS will work.

---

### Post by drigloi on 2005-10-08
I know it doesn't really belong to Hoary threads but today I've set up The Breezy Badger RC and now I have difficulties compiling the ufsd module.

```
root@ubuntu:/usr/src/ufsd# ./install.sh
configure kernel
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
scripts/kconfig/conf -s arch/i386/Kconfig
#
# using defaults found in .config
#
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make: gcc-3.4: Command not found
  CHK     include/linux/version.h
ufsd driver can be compiled for kernel 2.6.12(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was build and will be installed for kernel 2.6.12 but current kernel in 2.6.12-9-386.
Moving module in destination directory...
`./objfre/ufsd.ko' -> `/lib/modules/2.6.12/kernel/fs/ufsd/ufsd.ko'
Finding module dependencies...
I think you are using a Debian-like system
can't load ufsd module

```

It is obvious that gcc version causes the problems (Badger has gcc4 while Hoary used gcc3.x). Is there a way I can compile this with gcc4?

---

### Post by Snocrash on 2005-10-08
I know it might seem like overkill...but because I need to compile custom modules....Paragon-ntfs, ndiswrapper, nvidia or ati drivers, linux-wlan-ng, etc....I will almost always compile my own kernel after install. Even if I just use the stock config file from the distro, things will always build smoother and there is no question about having everything you need and the correct versions needed on the system to build the modules. It really does not take that long to do (30 mins to an hour on a good machine). And besides, building your own kernel is kinda a right of passage for n00bs. Below is a link to the kernel compile howto. I strongly suggest using the ubuntu patched sources with the --initrd flag just to eliminate filesystem issues at boot.

[Kernel compile howto]("http://www.ubuntuforums.org/showthread.php?t=56835")

Best of luck.

 -Sno

---

### Post by drigloi on 2005-10-08
Snocrash, you mean you're successfully running Paragon NTFS under Ubuntu Breezy Badger? If so I'll compile my own kernel at once :)

---

### Post by Snocrash on 2005-10-08
No...it was just a suggestion... I am running it under Hoary, but I have upgraded my gcc to 4.0 and glib to 2.0...so I did need to recompile everything including the kernel.

 -Sno

---

