---
title: "Installing a .tar file in 16.04"
date: 2016-11-16
forum: General Help
---

### Post by notso23 on 2016-11-16
I am new to Ubuntu and trying to install Blue Griffon but all the searched that I have done on the internet didn't work, I think they were old posts.

If someone can give a very basic steps to do this I would be so happy as it is driving me crazy. :D

I am trying to learn how to use the Terminal but it is slow, very slowly sinking in.

---

### Post by howefield on 2016-11-16
Thread moved to the "*General Help*" forum.

---

### Post by howefield on 2016-11-16
Have you downloaded the tar.bz2 file from the BlueGriffon website ?

If so, and it is downloaded to your Downloads folder, use the following terminal commands to run it..

```
cd ~/Downloads
```
```
tar -xjf ~/Downloads/bluegriffon-2.1.1.Ubuntu16.04-x86_64.tar.bz2
``` 
```
~/Downloads/bluegriffon/bluegriffon
```

---

### Post by notso23 on 2016-11-16
Thank you for your quick reply, I will try that.

---

### Post by notso23 on 2016-11-16
Well it installed with errors (see attached file) and now I would like to know how to remove it and download and install a new one.

One question, is using a command the same as using the terminal because I looked in Ask Ubuntu and I tried what they had to say and that didn't work either. 

Maybe the download is corrupted and that is why I want to clean up and start from scratch.

---

### Post by oldos2er on 2016-11-16
I'm a little confused; BlueGriffon doesn't install using your package manager, as howefield said you download it from the website, extract the contents into a folder then run the executable. The apt-get error would have an entirely different cause.

Yes, running commands is how one uses the terminal.

---

### Post by notso23 on 2016-11-16
> extract the contents into a folder then run the executable
Well you lost me here, I don't know what the executable file looks like in Ubuntu.

I will follow howefeilds instructions with a new download.

Is the package manager you mentioned is the same as the archive manager? because that extracts the files.

When I unpack the .tar file and put it on the desktop it is no longer a .tar file to follow howefields advice.

UPDATE
Still the same. But I don't know how to clean it up and remove the error symbol from the top bar and how to uninstall the program.

I was only looking at an html wysiwyg editor and to learn how to install them as I like to play with editing programs from html to ico files etc.

Thank you all for your help.
Shane :KS

---

### Post by howefield on 2016-11-17
> **notso23 said:**
> Well you lost me here, I don't know what the executable file looks like in Ubuntu.

The file called bluegriffon that is inside the folder that you unpacked is the executable. 

> I will follow howefeilds instructions with a new download.

They do work although you will see a fair bit of output in the terminal, I tested to double check before posting. If you haven't followed them, then fine but you get to keep all the pieces :)

> Is the package manager you mentioned is the same as the archive manager? because that extracts the files.

The package manager generally means something like Ubuntu Software Centre, or Synaptic Package Manager or Gdebi - an application that handles deb packages, the archive manager is exactly what it implies, something akin to Winrar or Winzip in Windows if you are familiar with that.

> When I unpack the .tar file and put it on the desktop it is no longer a .tar file to follow howefields advice.

So, skip the untar command then and run the executable with the third command posted.

> UPDATE
Still the same. But I don't know how to clean it up and remove the error symbol from the top bar and how to uninstall the program.

Just delete the folders that were created as a result of you unpacking the tar.bz2

---

### Post by notso23 on 2016-11-17
Thank you howefield for your advice, I have stumbled along and getting there slowly. I managed as you said, to remove the folders and I found that apt-get was stalled in Ubuntu Software Centre and all is fixed now.
I am now playing around with theme's etc as I found [http://www.ubuntufree.com](http://www.ubuntufree.com) and am looking at commands :P

---

### Post by oldos2er on 2016-11-17
Glad your problem is solved. Would you please use Thread Tools at the top of the page to mark it 'Solved' so that others may be helped by the solution? Thanks.

---

