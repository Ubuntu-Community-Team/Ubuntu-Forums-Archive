---
title: "have problem error unknown filesystem grub"
date: 2017-01-20
forum: General Help
---

### Post by samiaa71 on 2017-01-20
hello mates

i have problem in my pc when i was installing new ubuntu

then crashes so was abliged to reboot manually after i did that it shows me this problem now

error unknown filesystem grub
i followed some topics  from net but i dont succeed


now when i type this

ls  
shows

(hd0) (hd0,gpt1)

please what shall i do to fix this problem

---

### Post by speartip on 2017-01-20
Do you have any other systems installed on your computer? If so you could use a live session disk, to reinstall grub.
Or try reinstalling again, if successful, this time Grub will install itself to your mbr.

---

### Post by samiaa71 on 2017-01-20
no my dear [ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1776664_4.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1776664") 				 				 					 						 	[**[COLOR=#000000]speartip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1776664") 

i just use ubuntu inside is new pc

and not aloww me again any other option to reinstall any other os

please if there is any other possible way 
thanx in advance

---

### Post by speartip on 2017-01-20
How are you trying to install Ubuntu? Live DVD or USB?
And your saying that there is nothing else installed on your computer? Not even Windows? Totally blank?

---

### Post by speartip on 2017-01-20
Actually if you have a new computer, post 2010 it likely has secure boot enabled. That may well be your problem.
If you google "ubuntu uefi" you will find a lot of info on what you need to do.

---

### Post by samiaa71 on 2017-01-20
no i was installing using usb 

now when i i want to do new installation it doesnt come again from usb or dvd
it shows this message

error unknown filesystem grub

---

### Post by speartip on 2017-01-20
> **samiaa71 said:**
> now when i i want to do new installation it doesnt come again from usb or dvd
it shows this message

error unknown filesystem grub

Thats because your computer isn't set to boot from usb 1st. So it's trying to boot from your hard drive.
When you reboot with your usb inserted, you need to press a key to enter the boot menu, before that message comes up, & then select your usb.
On my HP it's the esc button, but it may be one of the function buttons or Delete button on yours.
Google your model of computer & see what it is, then you can try reinstalling again.

---

### Post by samiaa71 on 2017-01-20
sorry my friend for disturbing you
but i already made all necessary measures

the 1st boot now is from usb 
but the pc as i told dont take the boot
i tried from dvd is also the same the problem is as i mentioned faild to boot
like destryoed boot

only one problem appears after i make manual restart to press the botton
to start make usual installation of any os
os error 

error unknown filesystem grub rescue

i hope you understand me but i will try now ot change other usb and test again will reply u in few minutes
thanx for patience and help

---

### Post by speartip on 2017-01-20
Once you get to the error message your boot has gone to far.
You need to enter the boot menu of your bios after a shutdown and boot from the usb manually.

---

### Post by samiaa71 on 2017-01-20
is still shown the same

error unknown filesystem
entering rescue mode

grub rescue

---

### Post by speartip on 2017-01-20
OK. Your problem might be Secure Boot/UEFI related.
Try some of the suggestions from here & try again.
[https://www.google.co.uk/#q=ubuntu+disable+secure+boot](https://www.google.co.uk/#q=ubuntu+disable+secure+boot)

---

