---
title: "Why can't I rename files on the desktop on ubuntu 22.04 (LTS)"
date: 2022-04-24
forum: General Help
---

### Post by thestrongfork on 2022-04-24
Hi,

I am running Ubuntu 22.04 on a VMware virtual machine.

I have a text file on the desktop that I want to rename, but for some reason when I press the rename button nothing happens.

Is this a bug that I can solve?
Or at least rename the file in a different way?

---

### Post by mIk3_08 on 2022-04-24
Try run this command in your terminal; To access terminal just press ctrl, alt + t in you Linux Ubuntu desktop or go to your installed application and find terminal. Then run the command below.
```
echo "This is a test" >~/Desktop/desktoptextfile.txt
```
Regards and Cheers.

---

### Post by Impavidus on 2022-04-24
I don't know about rename buttons. I do all file management from the command line.

Open a terminal and change to the desktop:```
cd Desktop
```The name could be something else if your computer hasn't been set to English.

Then rename the file:```
mv oldname newname
```The mv command can both rename files and move them to a different directory.

---

### Post by mIk3_08 on 2022-04-26
> **thestrongfork said:**
> Hi,
I am running Ubuntu 22.04 on a VMware virtual machine.
I have a text file on the desktop that I want to rename, but for some reason when I press the rename button nothing happens.
Is this a bug that I can solve?
Or at least rename the file in a different way?
You can also move your file by using this command below in your terminal.
```
sudo mv '/home/desktopusername/documents/filename' '/home/desktopusername/desktop' 
```
To access your terminal in your desktop you can directly press ctrl and alt + t or you can find it in your Linux Ubuntu installed applications. Regards and cheers.

---

### Post by Impavidus on 2022-04-26
> **mIk3_08 said:**
> You can also move your file by using this command below in your terminal.
```
sudo mv '/home/desktopusername/documents/filename' '/home/desktopusername/desktop' 
```
To access your terminal in your desktop you can directly press ctrl and alt + t or you can find it in your Linux Ubuntu installed applications. Regards and cheers.

But don't use sudo when you don't need it and keep in mind that Linux is case sensitive: desktop &#8800; Desktop.

---

### Post by ActionParsnip on 2022-04-26
What is the output of:
```

ls -la ~/Desktop/*

```

---

### Post by mIk3_08 on 2022-04-27
> **Impavidus said:**
> But don't use sudo when you don't need it and keep in mind that Linux is case sensitive: desktop &#8800; Desktop. Yes. sorry for that. you can change it then. you can easily then use mv to move any file to your desktop.
```
mv '/home/username/downloads/filename' '/home/username/Desktop' 
``` If you want to perform any administrative task use sudo then. Regards and cheers

---

### Post by ActionParsnip on 2022-04-27
The d in downloads needs to be capitalised

---

### Post by mIk3_08 on 2022-04-28
> **ActionParsnip said:**
> The d in downloads needs to be capitalised
Thanks ActionParsnip for the reminder. And this also can be followed in the nautilus folder names. I'm not particular in case sensitive when it comes to folders but when encounter some error like this I can easily manage it. Thanks and regards.

---

