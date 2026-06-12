---
title: "My system has gone beserk. Help me"
date: 2007-05-10
forum: General Help
---

### Post by a27 on 2007-05-10
I left XP for Ubuntu a week ago.
I've had a few problems but have been able to search this forum and get answers/solutions so far.

So far.

Today, after reading through a thread on best music players, I decided to install *Listen*.
Add/Remove programs (I'm not sure that's the name) told me that there was some kind of conflict and "to be honest, you should try Synaptics instead".

While I was making my purchase in the Synaptics shop, Synaptics said I couldn't install Listen without making some changes to the depositories in Preferences.

I tried to do that in Preferences and got an error message: E: The package lists or status file could not be parsed or opened. Similar to this geezer [http://ubuntuforums.org/showthread.php?t=438669](http://ubuntuforums.org/showthread.php?t=438669)

Anyway, I tried a fix I read somewhere on the forum (I can no longer find the link but I think I tried to clean something from the terminal) and re-started the computer.

Now, the computer is not running right. I hear lots of hard drive noise. The computer is not quite frozen but the mouse moves like it's break-dancing. When I move it in a sweep, there is lots of judder and all programs are responding this way.

I'm writing this message from a Windows notebook by the way, as the Ubuntu desktop is currently unusable.

Thank you in advance for what is sure to be a speedy resolution to this issue.

---

### Post by firebadger on 2007-05-10
If you can manage, open a command prompt, type "top" and tell us what the top item in the list is.  That should tell us the process that is gobbling all your resources.

---

### Post by a27 on 2007-05-10
> **firebadger said:**
> If you can manage, open a command prompt, type "top" and tell us what the top item in the list is.  That should tell us the process that is gobbling all your resources.

Right.
I couldn't do that (my screen had frozen completely, background was gone) so I re-started ( hardware power button) and did as you instructed.

There are 9 instances of apt-cache on top, each of them is using about 5% of CPU.

There are also a few (more than 3) instances of apport and lsb_release.

---

### Post by a27 on 2007-05-10
> **a27 said:**
> Right.
I couldn't do that (my screen had frozen completely, background was gone) so I re-started ( hardware power button) and did as you instructed.

There are 9 instances of apt-cache on top, each of them is using about 5% of CPU.

There are also a few (more than 3) instances of apport and lsb_release.

Xord and kswapd0 have also joined the top list with 5 and 4.6% respectively.

---

### Post by tgalati4 on 2007-05-10
Sounds like your machine is updating its aptitude database.  Let it finish and all will be well.  This trips up new folks.  With 21k and counting packages, the databases are large and take a while to index and cross reference with what you already have installed.

This is something you get used to.  Depending on your net connection and hardware, it could take several minutes.  If you are patient, you will be rewarded.

---

### Post by a27 on 2007-05-10
> **tgalati4 said:**
> Sounds like your machine is updating its aptitude database.  Let it finish and all will be well.  This trips up new folks.  With 21k and counting packages, the databases are large and take a while to index and cross reference with what you already have installed.

This is something you get used to.  Depending on your net connection and hardware, it could take several minutes.  If you are patient, you will be rewarded.


I left it for over 30 mins and got no further. I got tired of it and shut it down.
Can I tell it to update when I prefer? If not, I'll start it again now.

---

### Post by firebadger on 2007-05-10
It's clearly some problem with apt probably to do with debris left behind after that error.  I'm not exactly sure what you should do to clean up, but you could try some of the ideas in the thread you cited and hopefully somebody else who has seen this issue before will reply with some ideas here.
Best of luck.

---

### Post by a27 on 2007-05-10
> **firebadger said:**
> It's clearly some problem with apt probably to do with debris left behind after that error.  I'm not exactly sure what you should do to clean up, but you could try some of the ideas in the thread you cited and hopefully somebody else who has seen this issue before will reply with some ideas here.
Best of luck.

Thanks.
I'd do that but the computer becomes unusable less than a minute after booting up.

Is there an Ubuuntu "safe mode".

---

### Post by srt4play on 2007-05-10
Maybe try booting into recovery mode and:

apt-get install -f

You  boot in recovery mode by pressing escape when you see "press esc to enter the menu" and then choose recovery mode.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> Maybe try booting into recovery mode and:

apt-get install -f

You  boot in recovery mode by pressing escape when you see "press esc to enter the menu" and then choose recovery mode.

I did that.
All I get is:

Segmentation faultsts... 1%
root@A27:~#

---

### Post by srt4play on 2007-05-10
ouch. not good.

hmm the next thing I would do is boot with my Ubuntu cd into a live environment and run fsck on the system partition.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> ouch. not good.

hmm the next thing I would do is boot with my Ubuntu cd into a live environment and run fsck on the system partition.

What is fsck?
How do you run fsck?

---

### Post by srt4play on 2007-05-10
Actually after doing a search for "apt segmentation fault" here on the forums, I would try a couple other things first.

fsck = filesystem check ,

sudo fsck /dev/sd*   where sd* is the partition you want to run it on.

But boot back into recovery and do 

apt-get update

And report the result.

---

### Post by firebadger on 2007-05-10
Things are not going well.  I suspect your hard shutdown has corrupted some stuff in your filesystem.  It's not a good idea if you can possibly avoid it to just power off as ext3 is a [journaling filesystem]("http://en.wikipedia.org/wiki/Journaling_file_system").

You do seem to have a root prompt however.

If it is a fresh install and you aren't going to lose hours of painstaking config work, you may be as well just reinstalling.

---

### Post by a27 on 2007-05-10
> **firebadger said:**
> Things are not going well.  I suspect your hard shutdown has corrupted some stuff in your filesystem.  It's not a good idea if you can possibly avoid it to just power off as ext3 is a [journaling filesystem]("http://en.wikipedia.org/wiki/Journaling_file_system").

You do seem to have a root prompt however.

If it is a fresh install and you aren't going to lose hours of painstaking config work, you may be as well just reinstalling.

Unfortunately, a lot has happened since initial installation.
I cannot afford to re-install.

---

### Post by srt4play on 2007-05-10
And re-installing wouldn't provide the excellent learning opportunity we have here would it.  :)

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> But boot back into recovery and do 

apt-get update

And report the result.

It did a lot of stuff in about half a second. Lots of things seem to have downloaded.

Fetched 5B in 1s (5B/s)
Segmentation faultsts... 1%

---

### Post by srt4play on 2007-05-10
I just found this thread:

[http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault](http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault)

In it several people had the same problem and it looks like what fixed it was a recreation of the file /etc/apt/sources.list.

boot to recovery
cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list

Edit the file so it only has this line:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

Save the file with ctrl-o  exit the editor with ctrl-x

Run apt-get update again.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> cp /etc/apt/sources.list /etc/apt/sources.list.bak


bash: cp: /etc/apt/sources.list: Not a directory

---

### Post by srt4play on 2007-05-10
What is the output of 

ls /

and 

ls /etc/

---

### Post by a27 on 2007-05-10
> **a27 said:**
> bash: cp: /etc/apt/sources.list: Not a directory

Disregard this.
It worked with sudo.

---

### Post by srt4play on 2007-05-10
You shouldn't have to use sudo in recovery mode, because you are root.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> I just found this thread:

[http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault](http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault)

In it several people had the same problem and it looks like what fixed it was a recreation of the file /etc/apt/sources.list.

boot to recovery
cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list

Edit the file so it only has this line:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

Save the file with ctrl-o  exit the editor with ctrl-x

Run apt-get update again.

Hey, Hey, Hey!!!
It's looking sexy!!!

---

### Post by a27 on 2007-05-10
Oops.
Same segmentation 1%after the sexines of the download.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> What is the output of 

ls /

and 

ls /etc/

It's an 8 x 3 matrix of text.
Like a table.

I think the output is same in both cases.

Do you want the content?

---

### Post by a27 on 2007-05-10
> **a27 said:**
> Oops.
Same segmentation 1%after the sexines of the download.

In this case, it fetched 1072kB in 36s.

---

### Post by srt4play on 2007-05-10
Misleading sexiness is a bitch isn't it?

The output of 'ls /' and 'ls /etc' should not be the same.  

Post the output of both please.

And try:

apt-get clean

Also, found this:
[http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/](http://www.deanlee.cn/linux/apt-get-segmentation-faulty-tree/)

which suggests deleting all .bin files in /var/cache/apt

do that with:

rm -f /var/cache/apt/*.bin

and then run

apt-get update

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> apt-get clean

I get no error but no "response" either.

Just a root@a27:~#

---

### Post by a27 on 2007-05-10
ls /
bin         dev     initrd             lib                  mnt   root   sys   var
boot      etc      initrd.img       lost+found   opt    sbin   tmp  vmlinuz
cdrom   home  initrd.img.old  media           proc  srv     usr   v,linuz.old

---

### Post by a27 on 2007-05-10
Yes, you're right.
The output from ls/etc is a whole lot bigger/longer. I don't know what I saw before.

---

### Post by a27 on 2007-05-10
What is the output of this to look like:

cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list

I have some stuff from linuxmce (I tried an installation last week) and an [http://10.0.0.82](http://10.0.0.82) (commented out) besides the feisty and edgy stuff.

---

### Post by srt4play on 2007-05-10
Besides the feisty and edgy stuff?  You really shouldn't mix them like that. 

cp /etc/apt/sources.list /etc/apt/sources.list.bak 

just backs up the sources.list file so when you modify it you still have the original version.

nano /etc/apt/sources.list

opens the file in an editor to make changes to it.

Did you delete the .bin files in /var/cache/apt as I posted earlier?

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> Did you delete the .bin files in /var/cache/apt as I posted earlier?

Yes, I did.
It didn't make a difference.
faultsts 1%.

---

### Post by a27 on 2007-05-10
> **srt4play said:**
> I just found this thread:

[http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault](http://ubuntuforums.org/showthread.php?t=417366&highlight=apt+segmentation+fault)

In it several people had the same problem and it looks like what fixed it was a recreation of the file /etc/apt/sources.list.

boot to recovery
cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list

Edit the file so it **only **has this line:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

Save the file with ctrl-o  exit the editor with ctrl-x

Run apt-get update again.

Sorry.
I didn't read properly.
Earlier, I amended the file to include that line.

Now I have deleted all lines and added that one.

Computer seems to be okay now.:popcorn:

---

### Post by a27 on 2007-05-10
> **a27 said:**
> Today, after reading through a thread on best music players, I decided to install *Listen*.
Add/Remove programs (I'm not sure that's the name) told me that there was some kind of conflict and "to be honest, you should try Synaptics instead".

While I was making my purchase in the Synaptics shop, Synaptics said I couldn't install Listen without making some changes to the depositories in Preferences.

I tried to do that in Preferences and got an error message: E: The package lists or status file could not be parsed or opened. Similar to this geezer [http://ubuntuforums.org/showthread.php?t=438669](http://ubuntuforums.org/showthread.php?t=438669)


Hey,
Now I'm back to this error
'E:The package lists or status file could not be parsed or opened.'

---

### Post by a27 on 2007-05-10
Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing libwv2-1c2 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by srt4play on 2007-05-11
Check the last post in this thread:

[http://ubuntuforums.org/showthread.php?t=439900](http://ubuntuforums.org/showthread.php?t=439900)

about deleting all lines from /etc/apt/sources.list , and then going into synaptic and reactivating them there (settings --> repositories, place check mark by all entries on Ubuntu Software tab, except source unless you need it).   then hit reload button in synaptic.

---

### Post by a27 on 2007-05-11
Thanks,
That worked.
Synaptics now opens (launches).
However, when I hit "reload" I got this:
An error occured

The following details are provided:

E: Dynamic MMap ran out of room
E: Error occurred while processing libwv2-1c2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by a27 on 2007-05-13
Anybody?

---

### Post by tgalati4 on 2007-05-13
Even if you did get your system fixed would you trust it?  It sounds like a mixed repository corruption.  You may have some critical system libraries that are mixed between compatible versions.  This will certainly confuse apt and cause countless problems.

If you can boot a live CD and keep it running (that is no known hardware problem) then it's time to backup your /home to a USB stick or an external drive and wipe the primary drive and start again.

We've given 4 pages of forum advice.  That's usually a clue that it's time to start fresh.

At least we tried.  Of course I couldn't have been more wrong with "normal apt behavior".

I am noticing a trend in new forum posts:  it seems that we are seeing more edge cases, folks with oddball hardware, or severe OS abuse.  Trying to install OS X in VMWare via VNC on a 486 DX machine with 64MB of RAM.  It's as if the simple problems have been solved and most folks can fix them on their own with simple searches.  We are left with the pathological cases.

---

### Post by a27 on 2007-05-13
Anybody with proper helpful advice?

---

### Post by tgalati4 on 2007-05-13
A bump would help.

---

### Post by srt4play on 2007-05-14
> **a27 said:**
> Anybody with proper helpful advice?

Can you post the exact contents of your /etc/apt/sources.list ? So we can see where it stands now... clearing it out and putting only that one entry in it should have fixed that mmap ran out of room error.

---

### Post by a27 on 2007-05-19
> **srt4play said:**
> Can you post the exact contents of your /etc/apt/sources.list ? So we can see where it stands now... clearing it out and putting only that one entry in it should have fixed that mmap ran out of room error.

Here it is.

[PHP]# Pluto sources - start

deb http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
# Pluto sources - end[/PHP]

---

### Post by srt4play on 2007-05-19
And the output of 

```
ls /var/cache/apt/
```

---

### Post by a27 on 2007-05-20
```
:~$ ls /var/cache/apt/
archives  pkgcache.bin  srcpkgcache.bin

```

---

### Post by srt4play on 2007-05-20
```
rm /var/cache/apt/*.bin 
ls /var/cache/apt/
```

---

### Post by a27 on 2007-05-20
> **srt4play said:**
> ```
rm /var/cache/apt/*.bin 
ls /var/cache/apt/
```

I've done that.

I got this.
```

abiodun@Abbey:~$ sudo rm /var/cache/apt/*.bin 
Password:
abiodun@Abbey:~$ ls /var/cache/apt/
archives

```

What should I do next please?

---

### Post by srt4play on 2007-05-20
```
sudo apt-get update
```

If you still get errors about mmap ran out of room, I'm afraid I'm out of ideas.

---

### Post by a27 on 2007-05-20
```
abiodun@Abbey:~$ sudo apt-get update
Password:
Get: 1 http://archive.ubuntu.com feisty Release.gpg [191B]
Hit http://archive.ubuntu.com feisty/main Translation-en_GB
Ign http://archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty/restricted Translation-en_GB
Hit http://archive.ubuntu.com feisty/multiverse Translation-en_GB
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Fetched 1B in 0s (2B/s)  
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libwv2-1c2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by a27 on 2007-05-20
> **srt4play said:**
> ```
sudo apt-get update
```

If you still get errors about mmap ran out of room, I'm afraid I'm out of ideas.

This man has a similar error

[http://ubuntuforums.org/showthread.php?t=445468](http://ubuntuforums.org/showthread.php?t=445468)

In this case, Error occurred while processing **xbubble** (NewVersion1) rather than **libwv2-1c2** (NewVersion1)

Is there a way to adapt his solution to my problem?

---

### Post by srt4play on 2007-05-20
Did you try running the command in that thread?

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

---

### Post by a27 on 2007-05-20
> **srt4play said:**
> Did you try running the command in that thread?

```
sudo apt-get update -o APT::Cache-Limit=25165824
```

WooHoo!! :p:p:p;);):D:D

```
abiodun@Abbey:~$ sudo apt-get update -o APT::Cache-Limit=25165824
Password:
Get: 1 http://archive.ubuntu.com feisty Release.gpg [191B]
Hit http://archive.ubuntu.com feisty/main Translation-en_GB
Ign http://archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty/restricted Translation-en_GB
Hit http://archive.ubuntu.com feisty/multiverse Translation-en_GB
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Fetched 1B in 0s (2B/s)  
Reading package lists... Done
```

```
abiodun@Abbey:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common libgtk-jni libcairo-java libgii1 libglib-java libgii1-target-x
  libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
abiodun@Abbey:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common libgtk-jni libcairo-java libgii1 libglib-java libgii1-target-x
  libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
```

---

### Post by a27 on 2007-05-20
This goes out to srt4play
[IMG]http://www.strangecosmos.com/images/content/107195.gif[/IMG]

---

### Post by srt4play on 2007-05-20
```
sudo apt-get update
```

Do you still get the error with the above?

---

### Post by a27 on 2007-05-21
> **srt4play said:**
> ```
sudo apt-get update
```

Do you still get the error with the above?

Yes, I do.

```
abiodun@Abbey:~$ sudo apt-get update
Password:
Get: 1 http://archive.ubuntu.com feisty Release.gpg [191B]
Hit http://archive.ubuntu.com feisty/main Translation-en_GB
Ign http://archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://archive.ubuntu.com feisty/restricted Translation-en_GB
Hit http://archive.ubuntu.com feisty/multiverse Translation-en_GB
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Fetched 1B in 0s (5B/s)  
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Read error - read (14 Bad address)
E: The package lists or status file could not be parsed or opened.

```

---

