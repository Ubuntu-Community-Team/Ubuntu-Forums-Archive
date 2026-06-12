---
title: "Messed up upgrade...HELP!"
date: 2016-07-31
forum: General Help
---

### Post by seagiant on 2016-07-31
Hi,
      Had my computer running perfect with Ubuntu 14.04LTS.

Saw the 16.04 upgrade and thought I would try it.

Was in the process of downloading it and was getting interference from another program.

Decided to just log off to stop everything.

Now I can only get a black screen with the Terminal prompt?

Can not bring up the Desktop????

Guess i buggered it good.

Just ordered a Ubuntu 14.04LTS install disk from Amazon.

Will try to reinstall when I get it???

If anyone has an idea on this, I'm all ears! Thanks!

---

### Post by Bashing-om on 2016-07-31
seagiant; Welppppp ...

What can you boot to ; grub, login screen; recovery console, TTY1 terminal ?
If you can get some terminal somewhere .. then we can look at what might be done to salvage this install/upgrade.
Then depends on the time and effort you want to expend.

[INDENT][INDENT]with time, effort, and a liveDVD
[INDENT][INDENT][INDENT]'buntu is always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-07-31
Hi,
     It goes to the Terminal screen with a black background.

Ask for login and password which I give.

Have tried different commands to fix from looking up solution on Internet but nothing works to get me back to Desktop???

I don't have the live CD from Amazon yet!

Any ideas????

Thanks!

---

### Post by Bashing-om on 2016-07-31
seagiant; Sure !

From that login screen; key combo ctl+alt+F1 -> that gives you a console interface.
Login here with your credentials .
Now run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
Do these run clean ? If errors we will have deal with them ! From this console, you do not have the amenities of a terminal emulator, depending on the situation - we may have to get inventive to relay info . 

[INDENT][INDENT]small steps
[INDENT][INDENT]but we find out the condition the condition is in
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-07-31
Hi,
     Ok, no response on the ctl+alt+fi!

I did get responsises from the command lines, but I'm still on the black terminal page with no change????

Hi,
     Ok I rebooted...no change!

---

### Post by Bashing-om on 2016-07-31
seagiant; Unk uh ..

That be 
```

ctl+alt+F1

```
As a key combo where all keys are depressed at the same time.
where it is a one (1) after the 'F" .. as in the "F1" key !

Try again..

[INDENT][INDENT]see then if you succeed .
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-07-31
Hi,
     I understand, just a typo, tried it and NO response on that! Thanks!

---

### Post by Bashing-om on 2016-07-31
seagiant; K;

Then we back up a step back ....
Can you boot to grub's boot menu ?

From there we can try and boot to a terminal .

[INDENT][INDENT]more than one path
[INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-07-31
Hi,
      Yes, I can get to grubs boot menu!

---

### Post by Bashing-om on 2016-07-31
seagiant; Great .

Sorry for the delay .. evening chores.
OK, we got to grub .. try this.
At the grub boot menu with the next to current kernel selected to boot. press the 'e' key for edit mode ->
boot parameters screen; arrow down to the line starting with linux and containing "quiet splash" arrow across and replace these terms with the term text . no quotes .
Key combo ctl+x to continue the boot process to TTY1. 
Can you log into the system here at this interface ?

[INDENT][INDENT]if not this way
[INDENT][INDENT][INDENT]that way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-01
Hi,
     Did what you said, but I was still taken back to the black terminal screen...no change????

---

### Post by Bashing-om on 2016-08-01
seagiant; Welll..


Not enough info to make any determination .. what we do not know at this point is how far in the upgrade process you got .. and what stage you attained.
If still predominately 14.04 .. that last procedure to attain a terminal is valid .. BUT if at 16.04 we are talking systemd as the initiate system and the procedure has a variance, 
Try at the boot parameters screen instead of text, insert the term systemd.unit=multi-user.target ; removing quiet splash and all after .
If you can attain the TTY1 terminal in this manner, then we are looking at systemd as the initiate system .. and we will have to tell the system what services to activate ( networking for one ).

Presently our goal remains to activate a terminal .

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-01
Hi,
     Yes, you are correct!

It is now showing 16.04 LTS, instead of 14!

I will have to try later this evening as I am busy now!

Thank you very much!!!!

Hi,
     Ok did as you instructed.

Computer recongnizes change, but still took me back to black terminal screen????

Ubuntu 14.04LTS, CD coming in Thursday, might have to try that????

---

### Post by Bashing-om on 2016-08-02
seagiant; Ouch ....

Not looking good for the home team.

Are you sure that what you see after booting up from grub is only a black screen .. I fully expect a black screen with a prompt , awaiting you to input your credentials
a) your username that you assigned yourself
b) your password - that you assigned - where nothing will be returned to the screen when entered .

Now if you still can not activate TTY1, then we see what we can do from the recovery console - booted to from grub .

Else, yeah .. we must go deeper from a liveDVD.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
     Maybe we have a misunderstanding?

I get the Terminal screen asking for user name and password.

That is not a problem but that's all I can get???

I'm trying to get back the Desktop, I guess.

---

### Post by Bashing-om on 2016-08-02
seagiant;  Great .

Sorry for the delay ... I had to go rescue my daughter , car broke down .


From this terminal it is on you to tell the system what to do ! All you have here is a booted kernel .. and nothing else.

Ftom thjis terminal we can work to find out the status of the install .
Next is to enable and activate a Wired internet connection, and get a bit of system info.
at this terminal once logged into the system run:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service

```

Now we should have networking .. and I want to see what the soutce.list files are .
execute:
```

cat -n /etc/apt/sources.list | nc termbin.com 9999
tail -v -n +1 /etc/apt/sources.list.d/* | nc termbin.com 9999

```
The result is a URL back in terminal - pass these complete links back here .. and we access the files .. this saves you a whole bunch of typing  because in this interface you do not have the amenities of a terminal emulator .

Once we have a few preliminaries out of the way .. then we see what happens in starting the GUI layer of the operating system.
Does that make sense ?

[INDENT][INDENT]there is no magic pill
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
      Ok it's telling me "systemctl command not found"

Thanks!

---

### Post by Bashing-om on 2016-08-02
seagiant; Humm ...

Still on 14.04 ??? As systemctl is a 16.04 command.
What returns :
```

uname -r
cat /etc/issue
lsb_release -a

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
     ok, the fist command it does not recongnize?

Theother commands gave me Ubuntu 16.04.1LTS 

Code name xenial

---

### Post by Bashing-om on 2016-08-02
seagiant; Welll .. well ..

Now that is "something else" ..
Are you sure that you are logged into TTY1 .. and not at a Grub prompt (grub >) ?
As the system reports 16.04 .. but will not recognize " systemctl  " AND will not return that a kernel is loaded . I really think your best interest is served by a clean fresh install . At this point I would never have confidence in the reliability of this system.

I do suggest we go back and verify :
```

sysop@1404mini:~$ uname -r
3.13.0-92-generic
sysop@1404mini:~

```
Will not hurt my feelings in the least to go back and recheck the commands:
systemctl ??
what returns:
```

systemctl status
systemctl list-units

```


[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]the gain is not worth the cost
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
     Every command there, gave me, "command not found"

Thanks!

Hi,
     I hate losing everything, but lesson learned I guess!

Maybe when I get the Install CD you can help me reinstall 14.04LTS!

Thanks for the help!!!!

---

### Post by Bashing-om on 2016-08-02
seagiant; Hey !

Maybe have not lost your data ! ..

What we will do when you get that liveDVD is mount the install's partition from there and have a look and see what we can salvage.

That is no big deal to copy the data off, to say a USB thumb drive ?

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
     Thanks, I have a external hard drive I can use I guess!

That would be good, if possible! Thanks again!

---

### Post by Bashing-om on 2016-08-02
seagiant; Sure !

Glad to help ( as much as I can) .
When you have the liveDVD we will proceed and see what we can do.

[INDENT][INDENT]all in a days' work
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-02
Hi,
      I'll let you know!!!

---

### Post by seagiant on 2016-08-04
Hi,
      CD didn't come today, probably tomorrow!

BUMP!

---

### Post by Bashing-om on 2016-08-04
seagiant; Welp;

Patience is a virtue .

Good things come to those who " wait for it, wait for it ... wait "

[INDENT][INDENT]when it comes
[INDENT][INDENT][INDENT]we see what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-08-04
seagiant; Welp;

Patience is a virtue .

Good things come to those who " wait for it, wait for it ... wait "

[INDENT][INDENT]when it comes
[INDENT][INDENT][INDENT]we see what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
      I have the live DVD now.

I put it in and it will boot from it.

I am at the page where it says run with another system, or install Ubuntu 14.04LTS!!!

Waiting to see how we can make sure to save my files, movies, ect.!!!!

Thanks!!!

Hi,
     I'm wondering if I can just boot off the DVD, then get my desktop back and that will allow me to download my files, ect and THEN I can do a complete overhaul to get a good trouble free install????

Hi,
     Tried to just run off the disc tempoary and it did not work!

Kicked the disk player open and gave me a blank screen more or less???

Waiting to see what you have on this? Thanks!

---

### Post by Bashing-om on 2016-08-05
seagiant; OK ...

Let's start by "looking" and see what we have on the install that we can access.

In bios, change the boot order to boot the DVD.
Boot to the DVD boot menu and choose " try ubuntu" ... => complete the boot to the desktop .. will take some time to load the DVD into ram and decompress .. give it the time .
ctl+alt+t to gain a terminal interface .
in this terminal execute:
```

sudo parted -l
sudo fdisk -lu

```
And post these outputs.
So that I know what we are working with and we know in the install where the root partition is located.
Once we know this we set a mount point and then we mount that root partition; and have a proper "looksee" , from the liveDVD.

IF and only IF the file system is sane .. then there is hope still we can salvage this install .. but do not hold your breath . 

It is small steps .. and  it is your time and effort to gain the goal that you set. We will spend as much time and effort and you are willing to salvage this install, IF possible . we will see ... taking these small steps - one step at a time to know what we have . We do not beat on a dead horse. There is that point that it is not worth the time and effort and that possibility of a compromised operating system to continue. There is that point where it is the better thing to just save the data and take that nuclear option and RE-install . A good internet connection, and good backup procedure,, takes 40 minutes and done and over with . However, we welcome this situation as an opportunity to advance on the linux curve of learning.

[INDENT][INDENT]We see what is
[INDENT][INDENT][INDENT]then see what can be done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
     Ok, got to desk top and Terminal screen.

First command said,"Command not found".

Second command worked brought up....

Devic boot      start           End           Blocks                   ID                System

/dev / sda1   2048   1457889279        728943616                  83                Linix


That's only part of it, I have no way to load the actual screen???

---

### Post by Bashing-om on 2016-08-05
seagiant; Yuk .. on me ...

My bad ..
correct "part" to be:
```

sudo parted -l

```

And I really really have got to see these outputs, so that I know.,
Let's do this:
Install our pastebin tool:
```

sudo apt install pastebinit

```
Now xfer the info to our pastebin site:
```

sudo parted -l | pastebinit
sudo fdisk -lu | pastebinit

```
where the result is a URL back in terminal. pass that link back here and we can access the file(s) on the site.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
     I'm on a windows computer at work?

Hi,
      There is an option to install 14.04LTS with the installed 16.04LTS.

This will save my files.

Can that be done and then delete 16.04 LTS?????

Ok,
       I got on the internet on my computer let me see what I can do!!!

---

### Post by Bashing-om on 2016-08-05
seagiant; Certainly !
> **seagiant said:**
> Hi,
      There is an option to install 14.04LTS with the installed 16.04LTS.

This will save my files.

Can that be done and then delete 16.04 LTS?????

One can do this .. but why ?? The liveDVD will serve our purpose .. and not have the hassle of allocating space to a new install, and then removing the other install. Then again, I like having a 'buntu dual boot system:
My system:
> 
sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   102402438    51200195+  83  Linux
/dev/sdb2   *   102404096   204804095    51200000   83  Linux
/dev/sdb3       204806144   266246143    30720000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux
sysop@1404mini:~$ 

sysop@1404mini:~$ 

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie16.04" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdc1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$


This is 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
     Did the pastebinit but not getting back a URL link???

[http://paste.ubuntu.com/22349268/](http://paste.ubuntu.com/22349268/)

Wait try this

---

### Post by Bashing-om on 2016-08-05
seagiant; Yepper ...

That workie .. so we know indeed that the install's root partition is on sda1 .
Now we can "mount" it .
From the liveDVD ( or an alternate installed system - as the case may be )
terminal commands:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda1 /mnt/looksee
ls -al /mnt/looksee/seagiant

```
where "seagiant" is the actual username on that installed system.
Now one can move about, looking, to see what all requires copying off.
in that above output are the files you have in "your" home directory .. 

On can look at other directories by (C)hange (D)irectory to that location>
say for example:
```

cd /mnt/looksee/Downloads

```

Now when done with this environment, as we MOUNTED it, it is our resposibility to take that mount back out of service, failure to do so .. "might" have some bad bad side effects .. in that we want the system flushed prior to bringing the system down.

Back out of what we have mounted:
```

sudo umount /mnt/looksee

```
Now you can power down or whatever other action you want to take outside of the installed system . The installed system is back to what it was .

Once your data is preserved, we look at what we can do to salvage this install ..

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
      That did not work to good???

[http://paste.ubuntu.com/22353927/](http://paste.ubuntu.com/22353927/)

---

### Post by Bashing-om on 2016-08-05
eagiant; Huh ?
> **seagiant said:**
> Hi,
      That did not work to good???

[http://paste.ubuntu.com/22353927/](http://paste.ubuntu.com/22353927/)

"That did not work to good???" does not relay much useful info . In what way and in what context 'did not work ' apply ?
What did you do, what did you expect, and what actually happened ? .. i see no fault with the output from 22353927 .
Looks fine to me that it also confirms we are working toward 'sda1' .

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
      Well I appreciate the help.

I just tried to reboot and got the black screen again.

Had to boot the live DVD to get back???

What's next???

---

### Post by Bashing-om on 2016-08-05
seagiant; Welp;

What next depends on where your mind is .. My mind is on mounting the install's root partition booting from the liveDVD
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda1 /mnt/looksee
ls -al /mnt/looksee/seagiant

```

Where are your thoughts ?

[INDENT][INDENT]we get on the same page
[/INDENT][/INDENT]

---

### Post by seagiant on 2016-08-05
Hi,
     Thanks, I'll see if I can figure something out with the DVD!

---

### Post by Bashing-om on 2016-08-08
seagiant; Hey !

Are you struggling ? 
Have I lost you ?
What is your status ?
Where do we go from here ?

[INDENT][INDENT]not going to leave you high and wet all over
[/INDENT][/INDENT]

---

