---
title: "USB-HD + intern-HD  PROBS!!(grubLoader) :("
date: 2007-12-19
forum: General Help
---

### Post by kulderzipke on 2007-12-19
Hi

I have a laptop with a **intern HD that has a WINDOWS XP pro** installation..
I don't want to touch anything on that HD because I want to boot from an external usb drive (320GB).

**The external HD is partitioned to a SWAP, a EXT3.** ( the rest is NTFS with all my old files..)
(used norton magic partition).** UBUNTU 7.10** is installed on those.. SWAP/EXT3.

When I boot from the laptop It goed to **GRUB** to chose your OS.
That's something I **don''t like** :( .. 

**_I want it to start windows xp pro without some preloaders.._**
[B][U]
ONLY when I go to BOOT-setup and chose "Boot from USB HARD DRIVE" it has to give a GRUB[/U][/B] so I can pick between the 3 linux options (generic recovery ..).
Else it doesn't even has to know there could be a linux installation.

Well I searched with google and on forums .. some Terminal-stuff..
[HTML]http://users.bigpond.net.au/hermanzone/[/HTML]

BUTTT..

Now It boots STILL grub but when I remove the USB HD and boot .. it gives errors.. probally because it needs the USB HD. And to boot WINXPpro I need to go to the boot setup and chose "Notebook Harddrive".

OK .. this is a long text :shock: Just want to give the full info..

Could someone help me or give me some advise ..
I really want to fix this!

 also some cmdos commands like fixmbr??

Anyways Thx !! Really appreciated if you even read this far :p And sorry for my bad english ^ ^

---

### Post by Toet on 2007-12-19
So if I understand correctly:

Windows had to start when you do not choose Boot from USB in boot-setup.

Grub has to start when you do chose Boot from USB in boot-setup.

Is this not exactly what is does at the moment?

---

### Post by kulderzipke on 2007-12-19
when I just start the laptop it has to go to windows (=intern HD) without a OSmenu

when I push F9 ( = boot menu) and select USB HARD DRIVE .. it has to boot from the harddrive (= ubuntu installation)

==>

when i start the pc it goes to grub => i select linux and it says error unmounth ... etc
so I tink it automatic tries to find the usbdrive instead of even looking at the internal drive.

when i go to Bootmenu (F9) => choose "Intern HD" it also goes to a GRUBmenu ..
- if I select windows, it  starts windows without a problem.
- if I select linux, it also start windows without a problem.

What I would like to have is this:

Do nothing => it boots from intern HD without a grubloader or something .. just how it was.

Go to Bootmenu and choose USB-HD => it boots from USB-HD with the GRUBloader-menu where I can only select the linux options.

anyways thx for your reply

---

### Post by Toet on 2007-12-19
What I think you have to do, is install Ubuntu onto the USB drive, and in the install use the option to install grub to the USB boot record instead of the master boot record (MBR). I think that option is under advanced when installing Ubuntu when you reach the grub part. But I'm not sure about the last part.

About the internal disk, you should use fixmbr from the xp cd.

---

### Post by kulderzipke on 2007-12-19
hmmz ok ill try that and reinstall ubuntu.. but what about the Grubloader where i need to go trough for windows.. 

do i have to do a fixrdm  or something.

thx

---

### Post by kulderzipke on 2007-12-19
okay I'm formatting EXT3 and SWAT and installing UBUNTU

The last step of the install-wizard had an advanced button => bootloader: 
I wrote: /dev/sdb5/

causs that's the root of the EXT3

so hopefully it boots from that partition :)
*fingers crossed*

anyways .. still need to find how to fix the windows boot :)


.. let you know in a few minutes what happened after install!

grtz

---

### Post by kulderzipke on 2007-12-19
no luck :s

same problems

i'm gonna try something with ultimate boot disk

---

### Post by Toet on 2007-12-19
> **Toet said:**
> About the internal disk, you should use fixmbr from the xp cd. .

---

### Post by kulderzipke on 2007-12-20
didnt work..

BUt I fixt everything with super grub disk (ultimate boot disk)

Then I took a screwdriver unplugged the battery and intern HD .. and let the notebook believe the usb was the internal disk => it wrote everything on the external as a primary partition

After that I plugged the HD and battery (used the Adapter) back  and now everything is perfect :)

anyway thx for your help!!

grtz

---

