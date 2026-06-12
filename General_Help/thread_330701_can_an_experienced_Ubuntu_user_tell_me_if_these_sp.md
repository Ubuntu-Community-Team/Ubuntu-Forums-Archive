---
title: "can an experienced Ubuntu user tell me if these speed tweaks are safe?"
date: 2007-01-03
forum: General Help
---

### Post by maddbaron on 2007-01-03
I found this here:
> [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

> Ubuntu Linux, unless you have set it up otherwise, uses the EXT3 system by default. It's a pretty good system. There are 3 journaling methods for EXT3 system.

    * Journal Data Writeback
    * Journal Data Ordered
    * Journal Data 

By default Ubuntu chooses "journal data ordered". In data=ordered mode, ext3 only officially journals metadata, but it logically groups metadata and data blocks into a single unit called a transaction. When it's time to write the new metadata out to disk, the associated data blocks are written first. data=ordered mode effectively solves the corruption problem found in data=writeback mode and most other journaled filesystems, and it does so without requiring full data journaling. In general, data=ordered ext3 filesystems perform slightly slower than data=writeback filesystems, but significantly faster than their full data journaling counterparts.

To speed it up, we are going to change it to the data=writeback system.
[edit]
Tweak

    * Open your Grub boot menu. 

sudo nano -w /boot/grub/menu.lst

    * Look for the Defoptions and Altoptions and make them look like the entry below. 

# defoptions=quiet splash rootflags=data=writeback
# altoptions=(recovery mode) single rootflags=data=writeback

    * You need to update your Grub since you have altered it. 

sudo update-grub

    * Now we are going to edit the Fstab because it will be expecting these options. 

sudo nano -w /etc/fstab

    * Now you are going to want to add the (data=writeback and noatime=0) flags to your hard drive. It might be a little confusing because of the new naming system. Look for the (,errors=remount-ro) and add it afterwards to make it look like our example. 

defaults,errors=remount-ro,data=writeback,noatime 0

    * Now you tell your system to use them both. 

sudo tune2fs -o journal_data_writeback /dev/yourdrive

And you're done.


[edit]
Concurrent Booting
[edit]
About

Concurrent booting allows Ubuntu to take advantage of dual-core processors, as well as processors that hyperthread or multithread or what ever the different companies call it now.
[edit]
Tweak

    * These settings are located in your /etc/init.d/rc file. Lets open it up. 

sudo gedit /etc/init.d/rc

    * Look through the file and you will find CONCURRENCY=none. You want to change it to: 

CONCURRENCY=shell

And you're done.


[edit]
Swapping
[edit]
About

Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.
[edit]
Tweak

    * First we have to gain access to your /etc/sysctl.conf file. 

sudo gedit /etc/sysctl.conf

    * Just scroll to the bottom of the page and add the tag listed below. The number you want depends on how much ram you have and what you do with your system. Please read the about above this to make your decision. I have mine set to 0 on a dual core laptop with 1 gig of ram and have seen no issues and a good performance gain. 

vm.swappiness=0

And you're done.


[edit]
Broadband Internet
[edit]
About

These are various tweaks taken from various places. Here is an article that explains them all if you would like to read it in depth. [http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)
[edit]
Tweak

    * You have to open your /etc/sysctl.conf file back up again. 

sudo gedit /etc/sysctl.conf

    * Then again, scroll to the bottom and just add these lines to it. 

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

    * You have to reset your sysctl for these to take effect. 

sudo sysctl -p

And you're done.


[edit]
IPv6
[edit]
About

IPv6 is an internet protocol. Most of your software uses IPv4 though and it causes conflicts.
[edit]
Tweak

    * We are going to create a file. Paste this into a terminal. 

sudo gedit /etc/modprobe.d/bad_list

    * Then paste this into the file and save and exit the file. 

alias net-pf-10 off

And you're done.


[edit]
Boot Profile
[edit]
About

You have just made a lot of changes to your system. Re profiling your boot will reorganize it and make it faster on boots afterwards.
[edit]
Tweak

    * Reboot your PC.
    * When you come to your grub list, hit escape to see your grub menu.
    * Edit the topmost line and add the word below to the end of it. 

profile

    * Then just reboot the system. 



Any potential corruption problems or system breaking?

---

### Post by autocrosser on 2007-01-03
Well-I've used the noatime option for quite a while without problems--as for the rest--goldbuggy has a thread on the forum about this topic---you might look it up & post there---

---

### Post by maddbaron on 2007-01-03
oh ok i didn't know thank you very much.

---

### Post by ~LoKe on 2007-01-03
> **autocrosser said:**
> Well-I've used the noatime option for quite a while without problems--as for the rest--goldbuggy has a thread on the forum about this topic---you might look it up & post there---

Did you break the comma key?

---

### Post by ~LoKe on 2007-01-03
I just applied all those settings.  I'll report back after a reboot.

---

### Post by ~LoKe on 2007-01-03
Noticeably faster boot, no problems thus far.

---

### Post by Falcorian on 2007-01-03
I'm a little confused by the last one... What line would I add "profile" to?

---

### Post by yopnono on 2007-01-03
I did test this and on one machine and I just unplugged the power cord (for testing) and I had data loss.

On another machine I did also have data loss hard shutdown just to test.
So if you have a power loss or a hard shutdown then you may have data loss.

---

### Post by ~LoKe on 2007-01-03
> **Falcorian said:**
> I'm a little confused by the last one... What line would I add "profile" to?

They left out a step.  When you reboot, and the grub thing comes up and starts counting down, hit "Esc" and you'll see a page with all your kernel booting options.  Use the arrow keys to move down to the kernel you use, then hit "e" and it'll let you edit the line.  Add the word "profile" to the end of that line, then his "Esc" again, then "b".

---

### Post by zgornel on 2007-01-03
> **yopnono said:**
> I did test this and on one machine and I just unplugged the power cord (for testing) and I had data loss.

On another machine I did also have data loss hard shutdown just to test.
So if you have a power loss or a hard shutdown then you may have data loss.
This should be recommended for laptops where tehre is no such risk.

---

### Post by Falcorian on 2007-01-03
> **~LoKe said:**
> They left out a step.  When you reboot, and the grub thing comes up and starts counting down, hit "Ecs" and you'll see a page with all your kernel booting options.  Use the arrow keys to move down to the kernel you use, then hit "e" and it'll let you edit the line.  Add the word "profile" to the end of that line, then his "Esc" again, then "b".

Ah, thanks, got it working now! :) Boot does seem noticeably faster.

---

### Post by ~LoKe on 2007-01-03
> **Falcorian said:**
> Ah, thanks, got it working now! :) Boot does seem noticeably faster.

You should do it every time you make a considerable change (ie. installing a new kernel).

---

### Post by Falcorian on 2007-01-03
> **~LoKe said:**
> You should do it every time you make a considerable change (ie. installing a new kernel).
Good to know! Thanks again!

---

### Post by autocrosser on 2007-01-03
I was on break at work on a windoze machine, so I tend to pound things out as fast as possible ;)

> **~LoKe said:**
> Did you break the comma key?

---

### Post by rsambuca on 2007-01-04
:frown: hmmm...  Tried changing the CONCURRENCY=none to "shell".  Borked my system.  Got a boot-up error.   rc??

Anyways, changed it back and still get the same error.  Not happy.

Can't find a fix anywhere.  Anyone have any ideas before I re-install?

---

### Post by ~LoKe on 2007-01-04
You must have done something else, or changed the wrong line if the problem still occurs.

---

### Post by rsambuca on 2007-01-04
That's what I figured as well, so I ended up copying the file from a kubuntu installation I had on another partition.  Still doesn't boot.

---

### Post by ~LoKe on 2007-01-04
> **rsambuca said:**
> That's what I figured as well, so I ended up copying the file from a kubuntu installation I had on another partition.  Still doesn't boot.

Perhaps with the exact error message we could help.  Take a picture if you have a camera.

---

### Post by rsambuca on 2007-01-04
Thanks, any help is much appreciated.

Just in case you can find something, here is the /etc/init.d/rc file:

```
#! /bin/sh
#
# rc
#
# Starts/stops services on runlevel changes.
#
# Optimization: A start script is not run when the service was already
# configured to run in the previous runlevel.  A stop script is not run
# when the the service was already configured not to run in the previous
# runlevel.
#
# Authors:
# 	Miquel van Smoorenburg <miquels@cistron.nl>
# 	Bruce Perens <Bruce@Pixar.com>

PATH=/sbin:/bin:/usr/sbin:/usr/bin
export PATH

# Un-comment the following for debugging.
# debug=echo

# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none', 'shell' and 'startpar'
CONCURRENCY=none

# Make sure the name survive changing the argument list
scriptname="$0"

umask 022

#
# Stub to do progress bar ticks (currently just for usplash) on startup
#
startup_progress() {
    $@
    step=$(($step + $step_change))
    progress=$(($step * $progress_size / $num_steps + $first_step))
    if type usplash_write >/dev/null 2>&1; then
        usplash_write "PROGRESS $progress" || true
    fi
}

#
# Start script or program.
#
case "$CONCURRENCY" in
  none)
	startup() {
		action=$1
		shift
		scripts="$@"
		sh=sh
		# Debian Policy §9.3.1 requires .sh scripts in runlevel S to be sourced
		# However, some important packages currently contain .sh scripts
		# that do "exit" at some point, thus killing this process.  Bad!
		#[ S = "$runlevel" ] && sh=.
		for script in $scripts ; do
			case "$script" in
			  *.sh)
				if [ "." = "$sh" ] ; then
					set "$action"
					RC_SAVE_PATH="$PATH"
					startup_progress $debug . "$script"
					PATH="$RC_SAVE_PATH"
				else
					startup_progress $debug $sh "$script" $action
				fi
				;;
			  *)
				startup_progress $debug "$script" $action
				;;
			esac
		done
	}
	;;
  shell)
	startup() {
		action=$1
		shift
		scripts="$@"
		sh=sh
		# Debian Policy §9.3.1 requires .sh scripts in runlevel S to be sourced
		# However, some important packages currently contain .sh scripts
		# that do "exit" at some point, thus killing this process.  Bad!
		#[ S = "$runlevel" ] && sh=.
		backgrounded=0
		for script in $scripts ; do
			case "$script" in
			  *.sh)
				if [ "." = "$sh" ] ; then
					set "$action"
					RC_SAVE_PATH="$PATH"
					startup_progress $debug . "$script"
					PATH="$RC_SAVE_PATH"
				else
					startup_progress $debug $sh "$script" $action
				fi
				;;
			  *)
				startup_progress $debug "$script" $action &
				backgrounded=1
				;;
			esac
		done
		[ 1 = "$backgrounded" ] && wait
	}
	;;
  startpar)
	startup() {
		action=$1
		shift
		scripts="$@"
		sh=sh
		# Debian Policy §9.3.1 requires .sh scripts in runlevel S to be sourced
		# However, some important packages currently contain .sh scripts
		# that do "exit" at some point, thus killing this process.  Bad!
		#[ S = "$runlevel" ] && sh=.
		# Make sure .sh scripts are sourced in runlevel S
		if [ "." = "$sh" ] ; then
			newscripts=
			for script in $scripts ; do
				case "$script" in
				  *.sh)
					set "$action"
					RC_SAVE_PATH="$PATH"
					startup_progress $debug . "$script"
					PATH="$RC_SAVE_PATH"
					;;
				  *)
					newscripts="$newscripts $script"
					;;
				esac
			done
			scripts="$newscripts"
		fi

		# startpar is not working as it should yet [pere 2005-09-10]
		[ -n "$scripts" ] && startup_progress $debug startpar -a $action $scripts
		startup_progress $debug startpar -a $action $scripts
	}
	;;
esac

on_exit() {
    echo "error: '$scriptname' exited outside the expected code flow."
}
trap on_exit EXIT # Enable emergency handler

# Ignore CTRL-C only in this shell, so we can interrupt subprocesses.
trap ":" INT QUIT TSTP

# Should we also output to the console?
# /proc won't be mounted if we don't have an initramfs, but then we're
# dealing with custom systems so it's their own fault that they'll get
# output from rcS ;)
if grep -w -q quiet /proc/cmdline 2>/dev/null; then
    QUIET=yes
else
    QUIET=no
fi
export QUIET

# Set onlcr to avoid staircase effect.
if [ "$QUIET" != yes ]; then
    stty onlcr </dev/console >/dev/console 2>&1
fi

# Now find out what the current and what the previous runlevel are.
runlevel=$RUNLEVEL

# Get first argument. Set new runlevel to this argument.
[ "$1" != "" ] && runlevel=$1
if [ "$runlevel" = "" ]
then
	echo "Usage: $scriptname <runlevel>" >&2
	exit 1
fi
previous=$PREVLEVEL
[ "$previous" = "" ] && previous=N

export runlevel previous

if [ S = "$runlevel" ]
then
	#
	# See if system needs to be setup. This is ONLY meant to
	# be used for the initial setup after a fresh installation!
	#
	if [ -x /sbin/unconfigured.sh ]
	then
		/sbin/unconfigured.sh
	fi
fi

. /etc/default/rcS
export VERBOSE

# Is there an rc directory for this new runlevel?
if [ -d /etc/rc$runlevel.d ]
then
	# Find out where in the progress bar the initramfs got to.
	PROGRESS_STATE=0
	if [ -f /dev/.initramfs/progress_state ]; then
	    . /dev/.initramfs/progress_state
	fi

	# Split the remaining portion of the progress bar into thirds
	progress_size=$(((100 - $PROGRESS_STATE) / 3))

	case "$runlevel" in
		0|6)
			ACTION=stop
			# Count down from 0 to -100 and use the entire bar
			first_step=0
			progress_size=100
			step_change=-1
			;;
	        S)
		        ACTION=start
			# Begin where the initramfs left off and use 2/3
			# of the remaining space
			first_step=$PROGRESS_STATE
			progress_size=$(($progress_size * 2))
			step_change=1
			;;
		*)
			ACTION=start
			# Begin where rcS left off and use the final 1/3 of
			# the space (by leaving progress_size unchanged)
			first_step=$(($progress_size * 2 + $PROGRESS_STATE))
			step_change=1
			;;
	esac

	# Count the number of scripts we need to run (for usplash progress bar)
	num_steps=0
	for s in /etc/rc$runlevel.d/[SK]*; do
            case "${s##/etc/rc$runlevel.d/S??}" in
                gdm|xdm|kdm|ltsp-client|reboot|halt)
                    break
                    ;;
            esac
            num_steps=$(($num_steps + 1))
        done

        step=0

	# First, run the KILL scripts.
	if [ "$previous" != N ]
	then
		# Run all scripts with the same level in parallel
		CURLEVEL=""
		for s in /etc/rc$runlevel.d/K*
		do
			level=$(echo $s | sed 's/.*\/K\([0-9][0-9]\).*/\1/')
			if [ "$level" = "$CURLEVEL" ]
			then
				continue
			fi
			CURLEVEL=$level
			SCRIPTS=""
			for i in /etc/rc$runlevel.d/K$level*
			do
				# Check if the script is there.
				[ ! -f $i ] && continue

				#
				# Find stop script in previous runlevel but
				# no start script there.
				#
				suffix=${i#/etc/rc$runlevel.d/K[0-9][0-9]}
				previous_stop=/etc/rc$previous.d/K[0-9][0-9]$suffix
				previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
				#
				# If there is a stop script in the previous level
				# and _no_ start script there, we don't
				# have to re-stop the service.
				#
				[ -f $previous_stop ] && [ ! -f $previous_start ] && continue

				# Stop the service.
				SCRIPTS="$SCRIPTS $i"
			done
			startup stop $SCRIPTS
		done
	fi

	# Now run the START scripts for this runlevel.
	# Run all scripts with the same level in parallel
	CURLEVEL=""
	for s in /etc/rc$runlevel.d/S*
	do
		level=$(echo $s | sed 's/.*\/S\([0-9][0-9]\).*/\1/')
		if [ "$level" = "$CURLEVEL" ]
		then
			continue
		fi
		CURLEVEL=$level
		SCRIPTS=""
		for i in /etc/rc$runlevel.d/S$level*
		do
			[ ! -f $i ] && continue

			if [ "$previous" != N ]
			then
				#
				# Find start script in previous runlevel and
				# stop script in this runlevel.
				#
				suffix=${i#/etc/rc$runlevel.d/S[0-9][0-9]}
				stop=/etc/rc$runlevel.d/K[0-9][0-9]$suffix
				previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
				#
				# If there is a start script in the previous level
				# and _no_ stop script in this level, we don't
				# have to re-start the service.
				#
				[ -f $previous_start ] && [ ! -f $stop ] && continue
			fi
			SCRIPTS="$SCRIPTS $i"
		done
		startup $ACTION $SCRIPTS
	done
fi

if [ S = "$runlevel" ]
then
	#
	# For compatibility, run the files in /etc/rc.boot too.
	#
	[ -d /etc/rc.boot ] && run-parts /etc/rc.boot

	#
	# Finish setup if needed. The comment above about
	# /sbin/unconfigured.sh applies here as well!
	#
	if [ -x /sbin/setup.sh ]
	then
		/sbin/setup.sh
	fi
fi

trap - EXIT # Disable emergency handler

exit 0


```

I'll reboot now into ubuntu to get the error message.

---

### Post by dannyboy79 on 2007-01-04
well if you said that you took the file from another install from another machine and that didn't fix it than there must be something else wrong right? I would just boot a live cd and take all the files you changed from the livecd and put them in your system, save the old bad ones in case you made other changes you can just compare them and make neccessary changes to new one to reflect the changes that you want to stay. might be confussing the way I have stated all this but it's a rather simple process. note all files you changed on your borked system, boot a live cd, create backups of all files that you changed by "renaming them", copy all files from live cd to correct locations. see if your borked system boots. if it does, now you can compare old file with new file and make any updates that you did want. good lcuk

---

### Post by rsambuca on 2007-01-04
Ok, tried rebooting again.  Grub gives me my selection screen.  Selected ubuntu.   Splash screen comes up briefly, then disappears, and the following two lines are displayed at the top of the screen:
> init: rcS process (1980) terminated with status 2
init: rc2 process (1986) terminated with status 2

Then everything just hangs there.  Any ideas?

---

### Post by rsambuca on 2007-01-04
Update...

Well, I don't know what happened, but I tried copying the modified files from other installations, I even tried copying the entire /etc/init.d folder.  Still had the same error.  I ended up just copying my home folder to a safe place, and re-installed Edgy from the live CD.  I then just re-copied my home folder back to the new installation and everything is pretty much back as it was.  Just had to reinstall a couple of programs, but other than that, relatively painless.

Sure wish I new what I did, though.  I have set up a few extra partitions for trying out different distros, so perhaps I will install an extra Edgy "test" system and see what I did!

---

