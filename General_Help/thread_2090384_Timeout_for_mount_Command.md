---
title: "Timeout for mount Command"
date: 2012-12-02
forum: General Help
---

### Post by terminator14 on 2012-12-02
The problem I'm having is actually on my OS X, but the mount command is used in Linux too, and I figured I would have a better chance of getting it answered here than an OS X forum. Anyway - I'm trying to have my Macbook Pro mount a few NFS shares at startup. Since the new version of OS X no longer has /etc/fstab, I have made a bash script that mounts the shares, and have told OS X to run the script at boot. The script looks something like this:

```
#!/bin/bash
umount /Volumes/Network/*

mount -t nfs -o resvport -w 192.168.1.10:/share /Volumes/Network/share/
```

This works great when my Macbook is at home, and the server (192.168.1.10) is available. Unfortunately, if I'm not home and I restart my OS X, instead of timing out in a few seconds, the script takes forever to get through so the boot hangs for a long time waiting for the script to finish.

Simulating what happens, I run something like:

```
time mount -t nfs -o resvport -w 192.168.1.11:/share /Volumes/Network/share/
```

where 192.168.1.11 is a random IP that is not assigned to any host. It takes 53 seconds for the command to exit. What's worse is, if the IP happens to belong to a Windows machine, it takes over 4 min for the command to complete. Considering that this is only a single mount command for a single share, and the script mounts multiple shares, each of which take equally long to timeout, this is a very big problem, as my Macbook can take 20 minutes to boot if the NFS server is not available. 

Is there any argument I can pass to the mount command to decrease the timeout value? The man page suggests several timeout arguments that the mount command excepts, but none of them seem to have any effect in this case.

PS. Yes, I'm aware I can make the script check what wireless network it's connected to, or see if the server is available before trying to mount its shares, but for now, I'm only interested in the timeout value for the mount command.

---

### Post by redmk2 on 2012-12-02
> **terminator14 said:**
> The problem I'm having is actually on my OS X, but the mount command is used in Linux too, and I figured I would have a better chance of getting it answered here than an OS X forum. Anyway - I'm trying to have my Macbook Pro mount a few NFS shares at startup. Since the new version of OS X no longer has /etc/fstab, I have made a bash script that mounts the shares, and have told OS X to run the script at boot. The script looks something like this:

```
#!/bin/bash
umount /Volumes/Network/*

mount -t nfs -o resvport -w 192.168.1.10:/share /Volumes/Network/share/
```

This works great when my Macbook is at home, and the server (192.168.1.10) is available. Unfortunately, if I'm not home and I restart my OS X, instead of timing out in a few seconds, the script takes forever to get through so the boot hangs for a long time waiting for the script to finish.

Simulating what happens, I run something like:

```
time mount -t nfs -o resvport -w 192.168.1.11:/share /Volumes/Network/share/
```

where 192.168.1.11 is a random IP that is not assigned to any host. It takes 53 seconds for the command to exit. What's worse is, if the IP happens to belong to a Windows machine, it takes over 4 min for the command to complete. Considering that this is only a single mount command for a single share, and the script mounts multiple shares, each of which take equally long to timeout, this is a very big problem, as my Macbook can take 20 minutes to boot if the NFS server is not available. 

Is there any argument I can pass to the mount command to decrease the timeout value? The man page suggests several timeout arguments that the mount command excepts, but none of them seem to have any effect in this case.

PS. Yes, I'm aware I can make the script check what wireless network it's connected to, or see if the server is available before trying to mount its shares, but for now, I'm only interested in the timeout value for the mount command.

I would think the combination of these would work ```
soft,retry=1
```...but I would not do it that way at all.

You could have the script check to see if the host you want is up (online) before before attempting a mount.  It would look something like this```
<hostname>=192.168.1.2

ping -c 1 "$HOSTNAME" > /dev/null

if [ "$?" -eq 0 ] ; then
  mmount ...
else
  send error to a log ...

```
In addition, I check for the presence of a readme file in the directory that serves as a the mount point like this ```
    if [ -f /path/to/mount/point/readme.nfs ]; then
   mount the exported share ...
```

If you are paranoid like me you would do both!

---

### Post by rnerwein on 2012-12-02
> **redmk2 said:**
> I would think the combination of these would work ```
soft,retry=1
```...but I would not do it that way at all.

You could have the script check to see if the host you want is up (online) before before attempting a mount.  It would look something like this```
<hostname>=192.168.1.2

ping -c 1 "$HOSTNAME" > /dev/null

if [ "$?" -eq 0 ] ; then
  mmount ...
else
  send error to a log ...

```In addition, I check for the presence of a readme file in the directory that serves as a the mount point like this ```
    if [ -f /path/to/mount/point/readme.nfs ]; then
   mount the exported share ...
```If you are paranoid like me you would do both!
hello
be aware of soft mounting a nfs-filesystem. it is not recommended for rw-mounts.
the result can be bad damaged data. if you do that you mount rd-only. nfs stack is
not on top and the results can be random.
cheers

---

### Post by terminator14 on 2012-12-02
> **redmk2 said:**
> soft,retry=1

I tried this on OS X and on debian - neither had a decreased timeout. This makes sense, since, according to the man page, the retry option defaults to 1 for soft mounts. To confirm this, I also tried retry=2, and sure enough, it took twice as long for the command to exit.

> **redmk2 said:**
> If you are paranoid like me you would do both!

I am, which is why I was planning on doing both an online host check and reduce the timeout of the mount command. The host online check that you did is pretty much how I'd do it too. The thing is - the same IP as my NFS server on my network can be assigned to a different machine on a different network, and both will happily respond to a ping. This means that in such cases, my macbook will still take 20 minutes to boot without a decreased timeout for the mount command. A combination of a ping check and a decreased timeout however should do just fine. Of course there are other things that can be done too, like checking the SSID of the wireless network the machine is connected to, but I want to figure out the timeout first and use that too, since I am just as paranoid as you.

> **rnerwein said:**
> hello
be aware of soft mounting a nfs-filesystem. it is not recommended for rw-mounts.
the result can be bad damaged data. if you do that you mount rd-only. nfs stack is
not on top and the results can be random.
cheers

That is pretty much what the man page says about soft mounts. Is there any way to reduce the timeout of a hard mount?

---

### Post by terminator14 on 2012-12-05
So far, the best I've found is using:

[http://www.bashcookbook.com/bashinfo/source/bash-4.0/examples/scripts/timeout3](http://www.bashcookbook.com/bashinfo/source/bash-4.0/examples/scripts/timeout3)

like:

```
timeout3 -t 10 mount -t nfs -o resvport -w 192.168.1.10:/share /Volumes/Network/share/
```

I haven't tested it thoroughly, but it seems to work. I don't really like this solution though, as it seems a bit unclean - using a script to kill the mount command.

Anyone know of a simple, clean way? Or perhaps someone can confirm that the mount command doesn't take an argument that can decrease its timeout.

---

### Post by redmk2 on 2012-12-05
> **terminator14 said:**
> ...I was planning on doing both an online host check and reduce the timeout of the mount command. The host online check that you did is pretty much how I'd do it too. The thing is - the same IP as my NFS server on my network can be assigned to a different machine on a different network, and both will happily respond to a ping.

This means that in such cases, my macbook will still take 20 minutes to boot without a decreased timeout for the mount command. A combination of a ping check and a decreased timeout however should do just fine. 

Of course there are other things that can be done too, like checking the SSID of the wireless network the machine is connected to, but I want to figure out the timeout first and use that too, since I am just as paranoid as you.
There are other ways of skinning the cat so to speak.  You can ping the hostname the NFS server.  Or you can check to see if the NFS server is running with something like this
```

    # Is the NFS daemon responding?
    rpcinfo -t "$FILESERVER" nfs &>/dev/null
```

You can see the entire WIki entry for the this script [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto")

---

### Post by terminator14 on 2012-12-05
> **redmk2 said:**
> There are other ways of skinning the cat so to speak.  You can ping the hostname the NFS server.  Or you can check to see if the NFS server is running with something like this
```

    # Is the NFS daemon responding?
    rpcinfo -t "$FILESERVER" nfs &>/dev/null
```

You can see the entire WIki entry for the this script [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto")

That's excellent - it's timeout of 5 seconds is much smaller than mount's timeout, and rpcinfo is built into OS X. I still have to test it at boot, but it should work perfectly (it works great from the command line) - thanks.

For anyone interested, here's the full script that I quickly whipped up:

```
#!/bin/bash

#Server 1 test
rpcinfo -t 192.168.1.10 nfs &>/dev/null
SERVER1_TEST="$?"

#Server 2 test
rpcinfo -t 192.168.1.11 nfs &>/dev/null
SERVER2_TEST="$?"

if [[ "$SERVER1_TEST" == 0 ]] && [[ "$SERVER2_TEST" == 0 ]]
then
        #Both servers were found to be running NFS
        umount /Volumes/Network/* &>/dev/null

        mount -t nfs -o resvport -w 192.168.1.10:/share1 /Volumes/Network/share1/
        mount -t nfs -o resvport -w 192.168.1.10:/share2 /Volumes/Network/share2/
        mount -t nfs -o resvport -w 192.168.1.11:/share3 /Volumes/Network/share3/
        mount -t nfs -o resvport -w 192.168.1.11:/share4 /Volumes/Network/share4/
fi
```

As you can see, I have 2 NFS servers I mount shares from, but it's easy enough to modify the script for a single server. This should work on both Linux, and OS X. If you are on OS X, and, like me, want to mount nfs shares at boot, create the folder ~/bin, put the script in it with a name like NFS_mount.sh, make it executable (sudo chmod a+x NFS_mount.sh), and run:

```
sudo defaults write com.apple.loginwindow LoginHook /Users/[username]/bin/NFS_mount.sh
```

While this should work great, if anyone figures out, or knows a way to decrease mount's timeout, please post here - I'm still curious.

---

### Post by terminator14 on 2012-12-08
While the above method works, it does have a bit of a disadvantage - if you start your laptop outside of the network which has your NFS server, the script will ignore the mount commands, and the NFS server shares will never get mounted.

A better way to do this is to tell the script to keep checking if the laptop becomes part of the network that has the NFS servers, and if it does, mount them. This means that if you start your computer somewhere else, as soon as you get home (assuming that's where your NFS server(s) are), it will mount the shares automatically.

```
#!/bin/bash

#Check if mount operation is already running
if ps -Af | grep mount_nfs | grep -viq grep
then
        echo 'Mounting already in progress' >&2
        exit 1
fi

umount /Volumes/Network/* &>/dev/null

#Attempt to mount the shares in the background. It will keep trying once per minute 10,000 times by default
mount -t nfs -o resvport,bg -w 192.168.1.10:/share1 /Volumes/Network/share1/ &>/dev/null &
mount -t nfs -o resvport,bg -w 192.168.1.10:/share2 /Volumes/Network/share2/ &>/dev/null &
mount -t nfs -o resvport,bg -w 192.168.1.11:/share3 /Volumes/Network/share3/ &>/dev/null &
mount -t nfs -o resvport,bg -w 192.168.1.11:/share4 /Volumes/Network/share4/ &>/dev/null &
```

---

### Post by steeldriver on 2012-12-08
a bit late to this thread, but is autofs available in OS X? I used a simple autofs setup in a similar situation and it worked quite well (basically the system doesn't attempt to mount the share(s) until a user attempts to access them)

---

### Post by terminator14 on 2012-12-08
> **steeldriver said:**
> a bit late to this thread, but is autofs available in OS X? I used a simple autofs setup in a similar situation and it worked quite well (basically the system doesn't attempt to mount the share(s) until a user attempts to access them)

I've heard about autofs many times before, but never did have occasion to use it. In this case, it might work good. Doing a quick search for OS X autofs, there are many articles that refer to autofs config files in OS X, but my latest version of OS X doesn't appear to have those. Either autofs was removed from the latest version of the OS for some reason, or they need to be created by hand. Either way, I'm sure there's a way to make it work. The idea itself is a good one, and one I'll definitely take a look at. Thanks for the hint.

---

