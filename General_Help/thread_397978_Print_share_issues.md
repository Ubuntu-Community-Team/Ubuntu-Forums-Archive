---
title: "Print share issues"
date: 2007-03-31
forum: General Help
---

### Post by mikebeecham on 2007-03-31
Hi there guys...I'm new to Linux and Ubuntu so I'll try and be as detailed as I can...

I have a PC, which I have partitioned off to run ubuntu...everything fine there.  On that machine I have an Epson R220 Photo Stylus printer, and everything is fine on that...Ubuntu recongised it off the bat and I can print locally.

Now...

I also have a second machine upstairs, which I running Ubuntu and can connect to the PC machine via a wireless router.  

Now, here's the issue....

When the PC machine I logged into Windows XP, the Ubuntu machine upstairs can connect to the PC and can print to the printer no worries.  However, when my windows/ubuntu machines is logged into Ubuntu, the Ubuntu machine upstairs can not find the printer at all.

Essentially, I want the Ubuntu machines upstairs to be able to print, no matter what the machine downstairs is logged in as.


I hope thats detailed enough..


Can anyone help a week-old linux user from tearing the remainder of his hair out?

---

### Post by acormack on 2007-04-01
I think i understand your setup.

Ubuntu PC upstairs needs to access the printer shared by downstairs PC which may be running either Ubuntu or Windows.

If PC downstairs is in windows then the upstairs PC is accessing a cifs share using samba client.

if PC downstairs is in ubuntu printer is probably shared using cups and so upstairs pc need to have second printer connection via cups to downstairs (ubuntu) pc.

The only way around this would be to install samba server on downstairs pc and share the printer as a samba (windows) share.

Again though, to make this work with a single printer definition on the upstairs pc you would probably have to have the downstairs pc with the same computername and sharename for the printer in both windows and ubuntu.

For me I would just have 2 different printer definitions on the upstairs pc and keep it simple.

hope this helps.

---

### Post by mikebeecham on 2007-04-01
Hi Acormack,

That sounds great.  Now, I've been using Linux for a little over a week, so if there's anyway that you (or someone else) could hand-hold me through this with instruction, then that would be great...

...I have no idea where to start!

---

### Post by acormack on 2007-04-01
Are you prepare to have 2 different printers on your upstairs PC

One called "downstairs windows printer"

and one called "downstairs cups printer"

---

### Post by mikebeecham on 2007-04-01
Nope....so there's no way I can use the printer downstairs wih the Linux machine upstairs, regardless of whether the printer machine is windows OR Linux?

---

### Post by acormack on 2007-04-01
The second option above is what you need:

<quote>
The only way around this would be to install samba server on downstairs pc and share the printer as a samba (windows) share.
</quote>

1. Install samba
2. give the linux server downstairs the same computername it has when booted in Windows
3. share the printer using the same share name as it has in windows
4. allow connection from the same username/password that you use for windows

Now the upstairs PC will not know whether the downstairs PC is booted in windows or LINUX

For Samba Instructions go here:

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

