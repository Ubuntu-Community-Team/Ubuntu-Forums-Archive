---
title: "Screwed up GRUB (error 17, 15, 23, 12) (prompt assistance appreciated)"
date: 2008-01-04
forum: General Help
---

### Post by Mnemonica on 2008-01-04
When I power up the computer it goes to the little "Dell" screen with the progress bar and that goes fine and fast like it should. Screen goes blank and then I get 

```
GRUB stage1_5

error 17
```

I'm currently using gutsy's live cd... I attempted the fix mentioned [here]("http://ubuntuforums.org/showthread.php?t=224351") but it gave me this

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd?,?)

Error 23: Error while parsing number

grub> setup (hd0)

Error 12: Invalid device requested
```

The only two reasons that I can think of for this happening is that windows might have updated (Eh?) or the fact that this laptop got left in the car overnight in sub-zero C temperatures. I'm not sure why the cold would affect it, but hardware isn't what I'm into so I'm not sure.

Thank you for your help in advance.

---

### Post by tgilber1 on 2008-01-05
Error 17 = could not get to stage 1.5 # My experience with Ubuntu is there is no file named stage1.5.  Instead, the following files are in the /boot/grub/ directory menu.lst, stage1, stage2, <filesystem>_stage1_5 (reiserfs_stage1_5), etc.

Error 15 = could not find image file

Error 23 = could not parse the block device (questions marks) info you gave, i.e. the question marks must be replaced with any value between 0 and 9.

Error 12 = Because you did not select a valid device with the root (hd?, ?), it could not write to the MBR of the disk.  You must select a valid disk with the root command before issuing the GRUB setup command.

Instead, you could try the following when you boot up

[LIST=1]
[*]When GRUB menu appears, press the <ESC> key
[*]Press the 'c' key to get to the GRUB interface 
# Note:  At the command prompt, you can type part of the command name and the "tab" key will finish the command or give you options if multiple choices exist
[*]find /grub/stage1 # if the file exist it should return a prompt. Do not trust the disk (hdx) info you get when running grub after booting linux, if you have multiple disk.  Do this process at the GRUB menu during bootup.
[*]If you get an error 15 for file not found, then the Linux image files probably do not exist.  If the find command returned disk and partition, the continue to the next step

ex. output # in the case of below, the stage1 file is on the disk 2, partition 1 - remember, first disk is 0.

grub> find /grub/stage1
find /grub/stage1
 (hd1,0)
grub> 

[*]root (hdx,x) # x=0-9, e.g., root (hd0,0)
[*]Once you find your partition with the image file, issue a setup (hdx), x=0-9 - eg., setup (hd0)
[*]Type reboot and hit the enter key
[/LIST]

Summary of GRUB commands

1.  find /grub/stage1
2.  root (hdx,x) - x=0-9
3.  setup (hdx) - x=0-9
4.  reboot

---

### Post by Mnemonica on 2008-01-06
> Instead, you could try the following when you boot up

   1. When GRUB menu appears, press the <ESC> key


Eh... I don't have a GRUB menu. There is no menu. Only a black screen with exactly what I said was there in the previous post.


```
GRUB stage1_5

error 17

```

I tried your suggestions in the terminal after issuing "grub" and I've tried every combination with no luck. Is there a way that I can just kill whatever was in the MBR and reinstall it without having to "recover" anything?

---

