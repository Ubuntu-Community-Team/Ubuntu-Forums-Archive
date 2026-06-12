---
title: "Ubuntu software will not open"
date: 2017-05-15
forum: General Help
---

### Post by Camilia on 2017-05-15
I click on the icon for Ubuntu software and it will not open. Any suggestions?

---

### Post by vasa1 on 2017-05-15
There are quite a few complaints about Ubuntu Software. I don't know why. I don't use it.

Instead, you can install Synaptic Package Manager:
```
sudo apt-get update
```and if that's error-free,```
sudo apt-get install synaptic
```and use that instead of "Ubuntu Software".

Or just use the terminal.

---

### Post by Camilia on 2017-05-15
I have the synaptic manager. I can't tell from the explanations which is the right program. In Ubuntu software the are clearer explanations of the programs. 

I am looking for a program to read an ebook.

---

### Post by vasa1 on 2017-05-16
> **Camilia said:**
> ...
I am looking for a program to read an ebook.
Two links that may be useful in helping you decide:
[http://www.omgubuntu.co.uk/2016/09/simple-gtk-ebook-viewer-app-linux](http://www.omgubuntu.co.uk/2016/09/simple-gtk-ebook-viewer-app-linux)
[https://www.maketecheasier.com/best-ebook-readers-for-linux-users/](https://www.maketecheasier.com/best-ebook-readers-for-linux-users/)

---

### Post by howefield on 2017-05-16
> **Camilia said:**
> I click on the icon for Ubuntu software and it will not open. Any suggestions?

Assuming that your installation is up to date, some threads have been solved with a reinstall of the application.

```
sudo apt purge ubuntu-software
```
```
sudo apt install ubuntu-software
```

---

### Post by Camilia on 2017-05-16
Well today I can open it.

---

### Post by Camilia on 2017-05-16
> **vasa1 said:**
> Two links that may be useful in helping you decide:
[http://www.omgubuntu.co.uk/2016/09/simple-gtk-ebook-viewer-app-linux](http://www.omgubuntu.co.uk/2016/09/simple-gtk-ebook-viewer-app-linux)
[https://www.maketecheasier.com/best-ebook-readers-for-linux-users/](https://www.maketecheasier.com/best-ebook-readers-for-linux-users/)
Thanks for the info. 

Googling I found FBReader. I haven't received my ebook yet so I haven't tried out how to work it. Seems complicated to me. Perhaps your suggestions will be easier. So far read at link that the options in Ubuntu software are out of date.

---

### Post by sp40140 on 2017-05-16
> **Camilia said:**
> I have the synaptic manager. I can't tell from the explanations which is the right program. In Ubuntu software the are clearer explanations of the programs. 

I am looking for a program to read an ebook.

Calibre is the answer.
Get it here:
[https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux)

---

### Post by Camilia on 2017-05-16
> **sp40140 said:**
> Calibre is the answer.
Get it here:
[https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux)
I don't feel comfortable with Calibre because of this 
[WARNING:]("https://calibre-ebook.com/download_linux") calibre is a highly complex piece of software with lots of very finicky dependencies. If you install from source, you are on your own. Please do not open bug reports or expect any form of support. You have been warned.

Well I found it in the synapse so I am going to download it from that source. 
Thanks a bunch all.

---

### Post by sp40140 on 2017-05-16
Yes. There is a warning. But I have been using it for many years. And never had any issues.
It IS a very complex software. But it's even more useful (at least to me). 
As far as I know it's been developed by a single person. And so not easy to provide support for all the users. (It's cross platform, works on windows as well). 
This is so useful that I would be willing to pay for it.

Not advertising it. Just how I feel about it after using it for many years.

---

### Post by Camilia on 2017-05-16
Well I can't use it for the ebook I am waiting on today. For it does not have my vendor, ecrates, in their list. 

Well it seems to have bypassed that page and has opened up. Perhaps I can use it. Got to try this when my sinus headache stops making my head feel like a balloon swaying back and forth in the wind.

---

### Post by Jorhel on 2017-08-31
> **howefield said:**
> Assuming that your installation is up to date, some threads have been solved with a reinstall of the application.

```
sudo apt purge ubuntu-software
```
```
sudo apt install ubuntu-software
```

I have the same problem I tried that and and got
 ```
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ sudo apt purge ubuntu-software
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'ubuntu-software' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-27 linux-headers-4.10.0-27-generic
  linux-headers-4.10.0-28 linux-headers-4.10.0-28-generic
  linux-headers-4.8.0-58 linux-headers-4.8.0-58-generic
  linux-image-4.10.0-27-generic linux-image-4.10.0-28-generic
  linux-image-4.8.0-58-generic linux-image-extra-4.10.0-27-generic
  linux-image-extra-4.10.0-28-generic linux-image-extra-4.8.0-58-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.

```
But it appears in my software list... 
I'll try to install synaptic

---

### Post by Andreyshel on 2017-08-31
> [COLOR=#000000]*sudo apt purge ubuntu-software. *[/COLOR][COLOR=#000000][I]
Try gnome-software
[/I][/COLOR]

---

