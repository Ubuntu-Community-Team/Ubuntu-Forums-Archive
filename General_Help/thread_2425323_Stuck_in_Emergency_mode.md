---
title: "Stuck in Emergency mode"
date: 2019-08-23
forum: General Help
---

### Post by ytterbious on 2019-08-23
Every time I boot into Ubuntu now, I am greeted with "You are in Emergency Mode" with the messages:
```
couldnt get size
```
```
no caching mode page found
```
and
```
assuming drive cache: write-through
```

It has been like this for about a month, mostly due to frustration and  not getting anywhere. I tried fsck to no avail, it didn't seem to do  anything when I ran it, if I recall correctly. Not sure if it was user  error or it just didn't need to be run. I want to say that I got stuck  in error mode after my computer got unplugged while running, but it has  been so long now I can't be completely certain.

Here's the journalctl log: [https://paste.ubuntu.com/p/Gk5BwWhP9q/](https://paste.ubuntu.com/p/Gk5BwWhP9q/)

---

### Post by Bashing-om on 2019-08-23
ytterbious - hey hey .

Tell us more about this sytem and the file system in use.
logical volume management ?
encryption ?

Why this boot parameter in /etc/default/grub:
```

radeon.cik_support=0 amdgpu.cik_support=1

```

And YUP - system is screaming and hollering that it can not verify the system files!
```

Aug 21 23:14:44 Sys-1 systemd-fsck[1008]: Ubuntu_18.04.02 contains a file system with errors, check forced.
Ubuntu_[color=red]18.04.02[/co;or]: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
fsck failed with exit status 4.
Failed to start File System Check on /dev/disk/by-uuid/6dfe2260-a4b9-4915-bbbd-dfc1ee46b02f.
Unit systemd-fsck@dev-disk-by\x2duuid-6dfe2260\x2da4b9\x2d4915\x2dbbbd\x2ddfc1ee46b02f.service has failed.
Aug 21 23:14:45 Sys-1 systemd[1]: Dependency failed for /home.
Aug 21 23:14:45 Sys-1 systemd[1]: local-fs.target: Triggering OnFailure= dependencies.

```

Unfortunately, if this is LVM, I do not have the experience to guide for a file system check/repair. Or maybe this is just a failure to mount the volumes ?

- A know-it-all, I am not -

---

### Post by ytterbious on 2019-08-24
Hey bashing-om, thanks for responding.

I know for a fact that the system isn't encrypted. Also, I'm pretty sure that it isn't using LVM because when I type ```
cat /etc/fstab
``` in the emergency mode terminal, I don't get any entries that look like /dev/mapper, they all look like /dev/sdX which tells me its a physical partition and not LVM correct?

Is a fsck really all I need to do? Would you mind telling me how?

---

### Post by Bashing-om on 2019-08-24
ytterbious; Great !

OK let's take a poke and see what we have to do.

show us:
```

sudo fdisk -lu

```
so we re-identify the target(s) to sic fsck on :)


[INDENT][INDENT]better safe than sorry
[/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-24
Alright, so now I'm having a separate problem where I will type in the following commands to copy the output to a .txt file and then copy it to my USB drive

```

sudo fdisk -lu > fdisk.txt
mount /dev/sdc1 /mnt/usb
cp -i fdisk.txt /mnt/usb

```

and I get (what I think is an error)

```
bash: Is a directory
```

because when I boot, I have either no file there or a file that is 0kb with no .txt extension.
For whatever reason, it worked earlier when I used the same commands, just with journal -xb > journal.txt instead (and it didn't have that little bash message either).

P.S. I'm doing this on a dual-boot win/ubuntu system so I'm sorry if it takes me a bit to respond, it's slow to restart and I keep having little issues like these.

---

### Post by Bashing-om on 2019-08-24
ytterbious; Hummm ...

well
try as:
does the mount point exist ?
```

ls -al /mnt/

```

then:
```

sudo mount /dev/sdc1 /mnt/usb/

```

No target directory in sdc1 ?
what shows:
```

ls -al /mnt/usb/

```

My fingers are crossed this is file system corruption - not hardware failure.

[INDENT][INDENT]it will be what it will be
[/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-24
You and me both!
So, I got it working. Somehow I was able to copy over the fdisk text this time, and if I had to guess, it didn't work before because this usb drive is getting pretty old now.

Output of sudo fdisk -lu
[https://paste.ubuntu.com/p/SrwhYHchFm/](https://paste.ubuntu.com/p/SrwhYHchFm/)

---

### Post by Bashing-om on 2019-08-24
ytterbious; :)

Cooking with Crisco now -

OK
1. Boot from the Ubuntu LiveUSB;
2. Open/Run Terminal;
3. Type in this terminal:
```
 
sudo fdisk -lu

```
 (to get the device name) - making sure our targets remain sda3 and sda4 then press ENTER;
4. Type:
```

sudo fsck /dev/sda3
sudo fsck /dev/sda4

```
It either of these error out - manual intervention - we can delve in deeper.
5. Restart the system and boot normally.

[INDENT][INDENT]all better now
[/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-25
Alright so that worked great, the system finally booted!

However, I'm now having an issue where my home directory is now only 19.5gb when it was originally around a terabyte.
When I open gparted to look a little more closely, I get
```
Unit -.mount does not exist, proceeding anyway.
Invalid MIT-MAGIC-COOKIE-1 key
(gpartedbin:27031): Gtk-WARNING **: 00:17:59.670: cannot open display: :0

```

Should I open a new thread for this or is it okay to stay here?

edit: When I check the size in nautilus it says 19.5gb, but when I use ```
sudo du -hs ~/

```
I get the whole 1.3tb. Weird.
It seems to be alright because when I install a game from Steam, it downloads it just fine. I did notice that it said it didn't have space to download before, but it seems to be working fine now for whatever reason.

The only thing I'm unsure about is that gparted error now.

---

### Post by Bashing-om on 2019-08-25
ytterbious; OH ...

I reckon we can stay here as the new issue may be related.

Let's look at the numbers:
post back:
```

sudo fdisk -lu
sudo parted -l

```

See where we go from here.

[INDENT]system with 
[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-25
sudo fdisk -lu
[https://paste.ubuntu.com/p/cS5QPhkPZR/](https://paste.ubuntu.com/p/cS5QPhkPZR/)

[FONT=arial]sudo parted -l
[https://paste.ubuntu.com/p/twVM3GVt9R/](https://paste.ubuntu.com/p/twVM3GVt9R/)[/FONT]

---

### Post by Bashing-om on 2019-08-25
ytterbious; Well -

Numbers look good - I do not see an issue.

After reboot all looks good ?

[INDENT][INDENT]just a glitch ?
[/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-25
sudo fdisk -lu
[https://paste.ubuntu.com/p/jZprN7GBSR/](https://paste.ubuntu.com/p/jZprN7GBSR/)

sudo parted -l
[https://paste.ubuntu.com/p/y4ZM8Vw7mZ/](https://paste.ubuntu.com/p/y4ZM8Vw7mZ/)

I also noticed that I get essentially the same error when I try ```
sudo gedit
```
```
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused

(gedit:4675): Gtk-WARNING **: 18:39:53.310: cannot open display: :0


```

---

### Post by Bashing-om on 2019-08-26
ytterbious; Dunno - yet -

Maybe "you" do not have full access rights to the GUI ?

Let's poke at it and see what we can find:
```

echo $XAUTHORITY
ls -al .ICEauthority .Xauthority

```

What shoes here for who has access rights ?

[INDENT]tight security
[/INDENT]

---

### Post by ytterbious on 2019-08-27
```
echo $XAUTHORITY

```
gives no output

```
ls -al .ICEauthority .Xauthority

```
gives me
```
-rw------- 1 valence valence 33304 Aug 27 15:49 .ICEauthority
-rw------- 1 valence valence    50 May 14 18:42 .Xauthority

```

---

### Post by Bashing-om on 2019-08-27
ytterbious; Hummm ...


Do not know what to make of your "echo $XAUTHORITY" result -
Mine:
```

sysop@x1804mini:~$ echo $XAUTHORITY
/home/sysop/.Xauthority
sysop@x1804mini:~$

```

Be aware that gedit is a GUI app, opening such with "sudo" is a no no;
See: [https://www.psychocats.net/ubuntu/graphicalsudo](https://www.psychocats.net/ubuntu/graphicalsudo)
And to compound things - with systemd gksudo is depreciated and the recommended replacement for gksu is 'pkexec'.

As I do not know the state of 'pkexec' in the default ubuntu desktop - we will have to poke here too.
what results now:
```

pkexec gedit

```
where I can accept that we may still have to install some enablement - maybe ?

Now we see if there remains an Authority issue.

[INDENT][INDENT]which way do we go
[/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-28
Yeah I thought it was a bit strange for it to be blank like that.
```
pkexec gedit
```

results in:

```
Unable to init server: Could not connect: Connection refused

(gedit:29940): Gtk-WARNING **: 00:52:22.676: cannot open display: 


```

And thanks for the tip. I knew sudo could mess permissions up, but I didn't really think about it when using it for GUIs.

---

### Post by Bashing-om on 2019-08-28
ytterbious; well
"Connection refused"

try:
```

sudo apt install nautilus-admin
pkexec gedit

```

Maybe
[INDENT]yes
[/INDENT]

---

### Post by ytterbious on 2019-08-28
nope, same output :/

```
Unable to init server: Could not connect: Connection refused

(gedit:26223): Gtk-WARNING **: 02:21:47.284: cannot open display:
```

---

### Post by Bashing-om on 2019-08-28
ytterbious; Humm ..

Sorta stuck here - if not obvious by now - I do not run Gnome as my DE of choice.
Is this only related to gedit with the failure to open the display ? Or any GUI application ?

As another test/poke:
what results:
```

gedit admin:///etc/default/grub

```
Or is it still required in Gnome that one has to create this file:
/usr/share/polkit-1/actions/com.ubuntu.gedit.policy
to allow policykit to interface with escalated privileges ?

[INDENT]ain't been there
[INDENT][INDENT]really do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-28
So far, I've noticed it happening with both gedit and gparted.

Running that command opens the grub text file just fine.

Huh yeah, I'm not sure. I'm still learning the ropes to be honest.

---

### Post by Bashing-om on 2019-08-28
ytterbious; Great - 

So we know it is a policykit thingy and to run a GUI app from terminal must be invoked with:
```

gedit admin:///<path>

```
in your use case/environment.

[INDENT]ubuntu
[INDENT][INDENT]fast moving target
[/INDENT][/INDENT][/INDENT]

---

### Post by ytterbious on 2019-08-28
I guess what confuses me is that, previous to this emergency mode business, gparted and gedit opened fine via terminal with just the command and entering my password.

I wonder what has changed.

---

### Post by Bashing-om on 2019-08-28
ytterbious; Well ...

Good question - That I have no response to.

As the original issue seems resolved -
how about you mark this thread "solved" and open a new thread - you can reference this thread - with this question to gain a wider audience.


[INDENT]a know-it-all I am not
[/INDENT]

---

### Post by ytterbious on 2019-08-28
Yeah that's a good idea.

And you may not be a know-it-all, but you are definitely very knowledgeable!

Thanks for all your help

---

### Post by Bashing-om on 2019-08-28
ytterbious;

LOL -

I keep an eye out for the new thread -
See what I can learn this day.

[INDENT][INDENT]always in that process
[INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

