---
title: "Shortcut/Link from Wine folder not working"
date: 2008-05-28
forum: General Help
---

### Post by Avinash.Rao on 2008-05-28
Hi Guys,

I am using Ubuntu 7 and i have installed Wine. After the installation of Wine i can see the wine menu under applications. I have installed Adobe Photoshop and Indesign. Wine has created a virtual folder C:\Program files\Adobe.

I created a shortcut on the desktop to Photshop.exe file located under c:\Program Files\Adbode\Photshop\..

The link or shortcut is created, but nothing happens when i execute this link. But, when i browse the folder and open photoshop.exe it works.

Can anyone help me create shortcuts for these applications on the desktop.

Thanks
Avinash

---

### Post by TeoBigusGeekus on 2008-05-28
If the path of your shortcut is
```
c:\Program Files\Adbode\Photshop\..
```
then it's wrong.
Open your /home folder and navigate to /.wine folder (press ctrl+H if you can't see it). Find the pseudo-program files/Adbode etc. folder, where the .exe should be situated, and copy the link to your shortcut.
Another thing is, you should enclose the shortcut with "" cause Ubuntu can't recognise window$ names (including spaces, i.e. Program Files).

---

### Post by Avinash.Rao on 2008-05-28
> **TeoBigusGeekus said:**
> If the path of your shortcut is
```
c:\Program Files\Adbode\Photshop\..
```
then it's wrong.
Open your /home folder and navigate to /.wine folder (press ctrl+H if you can't see it). Find the pseudo-program files/Adbode etc. folder, where the .exe should be situated, and copy the link to your shortcut.
Another thing is, you should enclose the shortcut with "" cause Ubuntu can't recognise window$ names (including spaces, i.e. Program Files).

Dear TeoBigusGeekus,

Thank you for your response.

I checked the properties of the shortcut, the link is /home/padma/.wine/drive_c/Program Files/Adobe/Photoshop 7.0.

I also created a new link after browsing through the .wine folder. Its still not working. How do i copy the link to the shortcut? Coz when i go to the properties of the shortcut, it just shows me the link, but i am not able to edit it.

Regards,
Avinash

---

### Post by TeoBigusGeekus on 2008-05-28
Don't forget to add ""
The shortcut should be
```
/home/padma/.wine/drive_c/"Program Files"/Adobe/Photoshop 7.0/nameofexe.exe
```

---

### Post by Avinash.Rao on 2008-05-28
I am sorry i am asking this again. Where do i add this link? I don't see any option or place to add this link. If i go to the properties of the link i created, nothing is changeable there.

Thanks again
Avinash

---

### Post by TeoBigusGeekus on 2008-05-28
Right click on Desktop and select Create Launcher. 
Type: Application
Name: Whatever
Command: wine /home/padma/.wine/drive_c/"Program Files"/Adobe/[COLOR="Red"]"Photoshop 7.0"[/COLOR]/nameofexe.exe

---

### Post by Avinash.Rao on 2008-05-28
> **TeoBigusGeekus said:**
> Right click on Desktop and select Create Launcher. 
Type: Application
Name: Whatever
Command: wine /home/padma/.wine/drive_c/"Program Files"/Adobe/[COLOR="Red"]"Photoshop 7.0"[/COLOR]/nameofexe.exe


Thank you so much, it worked! :)

---

### Post by roderick on 2008-05-28
Aestethically, you should quote the entire path just once...

wine "/home/padma/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/nameofexe.exe"

This is more accurate to each and every windows PATH which could contain many directories and/or filenames with spaces, and you wouldn't want to quote them individually.

Cheers

---

### Post by Avinash.Rao on 2008-05-29
Thank You :)

---

