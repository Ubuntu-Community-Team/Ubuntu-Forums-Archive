---
title: "X Won't Start; Urgent help needed"
date: 2006-12-30
forum: General Help
---

### Post by oa205 on 2006-12-30
Hello guys

can some1 pls help me?

I followed the original threadstarter's guide on this thread [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=fstab+is+bad](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=fstab+is+bad)

I was tryna configure my external nfts hard drive for read/write

now i i think i have crashed the whole system

X wont start for some reason now

I get a blue screen

i can get into the terminal.

tried to revert to my backup fstab file

but it wont let me cos of read only access

pls someone help me if u can

my email is [email]some_ayodele@yahoo.com[/email]

or pls post reply in this thread

thank you

---

### Post by strabes on 2006-12-30
chmod your backup fstab: ```
sudo chmod 777 /etc/fstab_backup
```

Then you should be able to copy it over your new one:```
sudo cp /etc/fstab_backup /etc/fstab
```

Assuming the name of your backup fstab file is called "fstab_backup"

Change "fstab_backup" to whatever you called the backup fstab file

---

### Post by scrooge_74 on 2006-12-30
Have you try to reconfigure the X server? 

sudo dpkg-reconfigure xserver-xorg

---

### Post by oa205 on 2006-12-30
thanx for quick reply

will try those nw

---

### Post by oa205 on 2006-12-30
> **strabes said:**
> chmod your backup fstab: ```
sudo chmod 777 /etc/fstab_backup
```

Then you should be able to copy it over your new one:```
sudo cp /etc/fstab_backup /etc/fstab
```

Assuming the name of your backup fstab file is called "fstab_backup"

Change "fstab_backup" to whatever you called the backup fstab file

sudo chmod 777 /etc/fstab_backup
that didnt work^ it said an operand was missing

i tried the next commands but it said cant create regular file read only system
:(

any further advice will be helpful

thanks

---

### Post by oa205 on 2006-12-30
help anyone ^^^

---

### Post by logos34 on 2006-12-30
> help anyone ^^^

[delete]

---

### Post by oa205 on 2006-12-30
can't do that

i got projects in C I can't lose.

If u can't help why step into the thread at all?

---

### Post by tseliot on 2006-12-30
Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by oa205 on 2006-12-30
ok im on it. thanks

---

### Post by oa205 on 2006-12-30
changed to vesa. at the end of the reconfigure it said "cannot create regular file /etc/X11/Xorg.Conf.20061230135443"

i cannot see anything wrong with my lspci, i will try to reproduce wot it says, because i had to copy down with pen and paper

0 0:0 0 .0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)

0 0:0.0 PCI Bridge: ATI Technologies Inc RS480 PCI Bridge

0 0:13:0 USB Controller: ATI Technologies IXP SB400 USB Host Controller

 0 0:13:1 USB Controller ATI Technologies IXP SB400 USB2 Host Controller

will stop there for now

---

### Post by bapoumba on 2006-12-30
Not sure I can help all the way, but if you are certain the problem is related to your fstab, when in recovery mode, **~# cat /etc/fstab** will show you the content of that file.
You can paste it in here, and your backup file too.

---

### Post by oa205 on 2006-12-30
> **bapoumba said:**
> Not sure I can help all the way, but if you are certain the problem is related to your fstab, when in recovery mode, **~# cat /etc/fstab** will show you the content of that file.
You can paste it in here, and your backup file too.

will it allow me edit the file tho?

cos right now main problem is file read access only

everything i do it always says file read access only

thnx for help anyway

---

### Post by bapoumba on 2006-12-30
**cat** just prints the file content on the screen. If you want to edit it, you need a text editor. **nano** is a small text editor that works in a tty. But first, copy the content of your fstab and your backup file in here.

---

### Post by oa205 on 2006-12-30
its soo hard because im using thesame laptop and i have to write it down. but i will get to it soon

but the main problem is it says fstab is bad in line 8

i want to restore fstab to fstab.bak, but it wont let me because of file read access only

thanks

---

### Post by bapoumba on 2006-12-30
To make it a little easier, and if you have internet access from ubuntu, get another tty open (CTRL+ALT+F2) login, and run **w3m [http://ubuntuforums.org](http://ubuntuforums.org)** or any other URL. w3m is a web browser that works in text mode ;)
Then you can copy and paste from one terminal to the other (switch between terminals with CTRL+ALT+Fx, x between 1 and 6. The 7th is the graphic session that does not work for you).

---

### Post by oa205 on 2006-12-30
will try that

merci mon ami :cool:

---

### Post by oa205 on 2006-12-30
upped

---

### Post by tseliot on 2006-12-30
> **oa205 said:**
> changed to vesa. at the end of the reconfigure it said "cannot create regular file /etc/X11/Xorg.Conf.20061230135443"
Did you boot in Recovery Mode?

Otherwise you will have to type the command with "sudo":
```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by oa205 on 2006-12-30
i did everything like u said

it just wont let me do anything because of read only access

i just want to copy over fsta backup to current fstab

dunno wot else to do

---

### Post by bapoumba on 2006-12-30
Well, do you have a live CD ? You can do it from there too.

---

### Post by oa205 on 2006-12-30
upped

---

### Post by tseliot on 2006-12-30
> **oa205 said:**
> i did everything like u said

it just wont let me do anything because of read only access

If you boot in Recovery Mode you are root therefore you have access to anything in your partitions.

Boot in Recovery Mode and try to copy the fstab.

---

### Post by oa205 on 2006-12-30
i have booted in recovery mode

it still wont let me do anything cos its read only 

i dunno wots wrong with it

fstab even looks ok to me 

but it keeps saying line 8 is bad

thanx for help anyway

---

### Post by tseliot on 2006-12-30
Then using a livecd (such as Ubuntu's) is the only solution I can think of.

1) Boot in a livecd
2) Open Terminal or Konsole and make a new folder in your userspace. For example:
```
mkdir data
```

3) mount your partition (let's suppose it's /dev/hda) in the "data" folder:
```
sudo mount /dev/hda data
```

4) Enter that folder:
```
cd data
```

Then you can modify the fstab by typing:
sudo nano -w etc/fstab

NOTE: it's not /etc/fstab but etc/fstab in this case.

---

### Post by oa205 on 2006-12-30
ok. will try that

thanks man

---

### Post by oa205 on 2006-12-30
> **tseliot said:**
> Then using a livecd (such as Ubuntu's) is the only solution I can think of.

1) Boot in a livecd
2) Open Terminal or Konsole and make a new folder in your userspace. For example:
```
mkdir data
```

3) mount your partition (let's suppose it's /dev/hda) in the "data" folder:
```
sudo mount /dev/hda data
```

4) Enter that folder:
```
cd data
```

Then you can modify the fstab by typing:
sudo nano -w etc/fstab

NOTE: it's not /etc/fstab but etc/fstab in this case.

i booted using the live cd. its a previous version from the one i got tho. its dapper i think

but yea i tried to create a directory but it didnt let me, same thing about the file permissions

---

### Post by oa205 on 2006-12-30
help

---

### Post by oa205 on 2006-12-30
upping

---

### Post by oa205 on 2006-12-30
come on someone ease my pain please

---

### Post by bulldog on 2006-12-30
Tell me how you got the idea your fstab has anything to do with your Xserver?
Because it hasn't.

You have a problem with the xorg.conf.

Stop panicking and think what you did before the Xserver stopt working.
In the blue screen you see when Xserver crashes,is a lot of information which is useful to resolve the problem.
Please read it carefully and see why Xserver is crashing.
If we know what is wrong we can solve it,otherwise it's just guessing what the problem can be and give you a lot of useless answers.

---

### Post by oa205 on 2006-12-30
> **bulldog said:**
> Tell me how you got the idea your fstab has anything to do with your Xserver?
Because it hasn't.

You have a problem with the xorg.conf.

Stop panicking and think what you did before the Xserver stopt working.
In the blue screen you see when Xserver crashes,is a lot of information which is useful to resolve the problem.
Please read it carefully and see why Xserver is crashing.
If we know what is wrong we can solve it,otherwise it's just guessing what the problem can be and give you a lot of useless answers.

all i remember was trying to install nfts-3g

i think i messed up fstab

cos even when i boot in recovery and go into the terminal, it wont let me edit anything

it says read only access

thats wot makes me tihnk its fstab

i dont remember doing anything with my Xserver 

well i installed beryl xgl last week. but that has been perfectly smooth, no problem at all

i can't tihnk of anything else

i did not alter xorg.conf either

---

### Post by bulldog on 2006-12-30
Well if you persist in replacing the fstab boot the live cd and mount your ubuntu install.
On which partition is your ubuntu,or if you don't know,boot the live cd and type in a terminal the next command and copy the outcome to the forum.
```
sudo fdisk -l (l as in like)
```
I can give you the mount commands and the copy command for your fstab

---

### Post by oa205 on 2006-12-30
> **bulldog said:**
> Well if you persist in replacing the fstab boot the live cd and mount your ubuntu install.
On which partition is your ubuntu,or if you don't know,boot the live cd and type in a terminal the next command and copy the outcome to the forum.
```
sudo fdisk -l (l as in like)
```
I can give you the mount commands and the copy command for your fstab

its working now :)

i used the live cd

replaced fstab with backup

everything good nw

its still linux for life

thnx guys :)

---

