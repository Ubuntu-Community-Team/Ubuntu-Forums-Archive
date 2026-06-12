---
title: "cant figure out how to copy file from my USB drive"
date: 2013-08-27
forum: General Help
---

### Post by robert22 on 2013-08-27
Cant figure out how to copy a single file (modem-diagnostics) from my thumb drive. I dont think I need to mount the USB drive because when I insert the usb drive into the notebook a window pops up and shows me the file. So I think its automounted. Please correct me if im wrong.

so under the command line I wanted to see the file on my usb drive the same way that I saw it in the pop up window by doing the following:

$ cd media/removable

So now Im in the removable directory and i type

$ dir

and I see USB\ Drive

so I decided to type: $ cd USB\

and this I see >

I have no idea what that means?

Im just trying to look at the file in the USB directory.

So my three questions are:

1) what does it mean when you get the > ?
2) How can i change the directory to USB to look at the file "modem-diagnostics"?
3) How can I copy "modem-diagnostics" from my USB to usr/local/bin via the command lines? WHATS THE CORRECT SYNTAX!:mad:

FYI usr/local/bin is created already, its just waiting for the file "modem-diagnostics"

Also I tried a few ways to get it to work and have not been successful. I list my attempts below. Maybe someone can tell me what im doing wrong.

1) sudo cp /media/removable\USB\Drive/ modem-diagnostics .
2) sudo cp /media/removable/USB/Drive\ modem-diagnostics .
3) sudo cp /media/removable/USB/Drive\ modem-diagnostics 
4) sudo cp /media/removable\ modem-diagnostics . 


Thanks in Advance.

---

### Post by jlh68 on 2013-08-27
Have you tried to "drag-n-drop" from the flash drive to your desktop?  When on your desktop you can put in the folder that you choose.

---

### Post by Bashing-om on 2013-08-27
robert22; Hi ! Welcome to the forum .
To address your questions:
1. the ">" character is a bash shell interpreter prompt when the shell saw "USB\" it went into "program mode" as what you entered was not a command to bash.
2. Depends on the version you have installed .. mounting locations have changed recently. Let do a slow walk through and see what is:
With your usb drive plugged in;
post the out put -between code (#) tags -  of;
```

ls -la /media/
ls -la /media/removable

```
depending on that out put is what will be advised to discover the response to
3. Pending

And yeah, the syntax in ubuntu is different than what you may be accustomed to -> It will not take long to become adjusted !

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-08-27
On *nix systems, the path separator character is a forward slash (/) - backslash (\) is for Windows - in *nix, \ is used for 'escaping' things like spaces and control characters, as well as a line continuation character. In particular, typing 

```
cd USB\ 
```

then hitting ENTER tells the shell you want to continue your cd command on the next line - the > is a prompt waiting for you to type more stuff, whereas

```
cd USB\ Drive
```

says "change to the directory (with a space in its name) called USB Drive". So what you probably need is

```
cp /media/removable/USB\ Drive/modem-diagnostics .
```

or

```
cp "/media/removable/USB Drive/modem-diagnostics" .
```

Note that 'sudo' shouldn't be necessary if you own '.' (the current directory)

---

### Post by robert22 on 2013-08-27
> **Bashing-om said:**
> 
With your usb drive plugged in;
post the out put -between code (#) tags -  of;

```

ls -la /media/
ls -la /media/removable

```
[INDENT][INDENT]
[/INDENT]
[/INDENT]


Does this help you?

/media/removable $ ls -la /media
total 4
drwxrwxrwt 4 root root 80 Aug 27 13:12 .
drwxr-xr-x 20 root root 4096 Aug 13 08:09 ..
drwxr-xr-x  2 root root 40  Aug 27 13:12 archive
drwxr-xr-x  3 root root 60 Aug 27 17:30 removable

/media/removable $ ls -la /media/removable
total 4
drwxr-xr-x 3 root    root       60 Aug 27 17:30 .
drwxrwxrwt 4 root    root      80 Aug 27 13:12 ..
drwxrwxrwx 1 chronos chronos 4096 Aug 27 15:01 USB Drive

---

### Post by Bashing-om on 2013-08-27
robert22' Hey !

Yeah .. what is throwing you is the space in "drwxrwxrwx 1 chronos chronos 4096 Aug 27 15:01 USB Drive"
USB Drive -> in linux a space is a delimiter.. 
try:
```

ls -la /media/removable/USB\ Drive

```
also keep in mind that linux is case sensitive ... "USB" is not the same same as "usb".
It would simplify things from ubuntu's perspective if you were to change that label to say "USB_Drive" getting rid of that space.

[INDENT][INDENT]we will get it right directly
[/INDENT][/INDENT]

---

