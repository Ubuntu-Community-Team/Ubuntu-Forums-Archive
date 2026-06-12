---
title: "How to create swap file on ext4"
date: 2014-05-04
forum: General Help
---

### Post by Chelidze on 2014-05-04
[COLOR=#333333][FONT=UbuntuRegular]My friend whats to create a 4GB swap file on his ext4 file system. because he is using a chromebook acer c7 the way he installed he did not have a chance to specify swap partition[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and now he want to create a swap file on his file system.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This is the guide he is following[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://ubuntuforums.org/showthread.php?t=1618220&p=10098565#post10098565](http://ubuntuforums.org/showthread.php?t=1618220&p=10098565#post10098565)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]First you have to create a 2GiB file, for example in /mnt:[/FONT][/COLOR]
```
sudo dd if=/dev/zero of=/mnt/swap bs=1M count=2048

```[COLOR=#333333][FONT=UbuntuRegular]Then format the file to swap:[/FONT][/COLOR]
```
sudo mkswap /mnt/swap

```[COLOR=#333333][FONT=UbuntuRegular]Add the swap file to the system:[/FONT][/COLOR]
```
sudo swapon /mnt/swap

```[COLOR=#333333][FONT=UbuntuRegular]Check it out, i.e.:[/FONT][/COLOR]
```
free -m

```[COLOR=#333333][FONT=UbuntuRegular]Edit the fstab file:[/FONT][/COLOR]
```
gksu gedit /etc/fstab

```[COLOR=#333333][FONT=UbuntuRegular]and add this line at the end of the file:[/FONT][/COLOR]
```
/mnt/swap  none  swap  sw

```[COLOR=#333333][FONT=UbuntuRegular]Save the file and exit. That's all.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][B]This is what he is getting
[/B][/FONT][/COLOR]
[IMG]http://i.stack.imgur.com/ahwRs.jpg[/IMG]

```
user@chrubuntu:~$ sudo swapon /mnt/swap
swapon: /mnt/swap: swapon failed: Invalid argument

```[COLOR=#333333][FONT=UbuntuRegular][B]and his fstab looks like this
[/B][/FONT][/COLOR]


[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/NNRgs.jpg[/IMG][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]any way to fix this ??[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]One more thing he is using ubuntu 14.04 and it is not a fresh install[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thank you for your time[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-05-04
That is strange.  Try using the *swapon* command with UUID

```
man swapon
```

---

### Post by Yellow Pasque on 2014-05-04
- There's nothing in the fstab so swapon probably won't work..
- Does /mnt/swap exist?
- Shouldn't '2048' have an M after it to specify MB instead of bytes?

---

### Post by HermanAB on 2014-05-05
Do yourself a favour and read:
$ man swapon

It is all explained nicely in there.

---

### Post by Chelidze on 2014-05-05
sorry every one as far as I understand it is using custome kernel [FONT=Ubuntu Mono]3.4.0 #1 SMP Fri Apr 11 19:07:10 PDT 2014 x86_64 x86_64 x86_64 GNU/Linux[/FONT] that can not use swap (at least that is what I think and [COLOR=#444444][FONT=UbuntuRegular]@psusi from askubuntu[/FONT][/COLOR] is the problem)

---

### Post by tgalati4 on 2014-05-05
Chromebooks are running on ARM architecture with solid state memory, so perhaps swap capability was removed from that kernel to save wear-and-tear.  You could recompile with swap capability added back in and use a USB stick for your swap location, in case swap really does trash the memory.

---

### Post by Shailender_Bhatia on 2014-09-30
Hi All -

Am a very user tto Ubuntu and while installing the ubuntu i did not create the swap partition and now i want to create one.
I am attaching the screenshot of my partition table and am trying to resize my ext4 so that i can create swap out of it but am unable to do so .

Please help.

Thanks!

---

