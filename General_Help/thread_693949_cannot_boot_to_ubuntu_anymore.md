---
title: "cannot boot to ubuntu anymore"
date: 2008-02-11
forum: General Help
---

### Post by shadow_yada on 2008-02-11
[FONT="Lucida Sans Unicode"]Hello!!
I need help
I have a dual boot computer windows XP and ubuntu 7.10:KS
I just use windows because of my family homework and games 
one of these days I had a problem with the windows OS It crash as usual and I had to reinstall it the only thing that I did not though about is that by reinstall windows having ubuntu there the boot sector of ubuntu gets overwritten or deleted by the MBR of windows no I cannot access ubunut ](*,) so I uninstalled windows again and nothing still not able to access ubuntu ](*,) 

What can I do:confused: is there a way to fix that and access ununtu w/o having to delete the OS ? 
can anyone help me with this, please ???:confused[/FONT]:

---

### Post by taurus on 2008-02-11
If you want to access Ubuntu partition, install fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

If you want to boot Ubuntu and XP, then reinstall GRUB to MBR since XP overwrote GRUB when you reinstalled XP.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by apetresc on 2008-02-11
Also, you can reinstall GRUB without needing to reinstall either XP or Ubuntu. Just use a LiveCD to restore GRUB. Instructions can be found here: [http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

---

### Post by xandorv on 2008-02-11
All of us run into this problem time and again. It is best to keep this utility called 'Super Grub Disk' in a CD. 

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

It basically allows you to handle all the MBR related problems including reinstalling GRUB, recovering your windows partition in those rare cases when GRUB simply doesn't display Windows etc. Its very easy to use and I hope more people use it. you only have to put it in your CD drive and reboot! 

The download file is small and you should burn it on a rewritable CD so that you can re-burn the updates when they come.

---

### Post by smriti on 2008-05-02
hi all
My ubuntu was working fine till yesterday.today when I started my system it's showing an error /etc/init.d/rc:2:sed:Input/Output error
I don't knw how to solve this.Plz help me.

---

