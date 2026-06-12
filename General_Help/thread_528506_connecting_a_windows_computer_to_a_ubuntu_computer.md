---
title: "connecting a windows computer to a ubuntu computer"
date: 2007-08-17
forum: General Help
---

### Post by sarahsilverman on 2007-08-17
i don't have a burner on my computer so i can't burn any dvd's. my cousins computer has one. i want to burn the iso from my computer using his dvd driver burner thing. someone told me all i have to do is connect the computers together and from my computer (ubuntu) i must point the burning program to the other computers dvd burner.

how can i do this? i have no idea, i tried but it just didn't work.

i have a cat5 crossover cable.

now i don't want to move the iso file, cause i can't. if i do it will be corrupted since it is written in a different format. rather i want to make use of my cousins dvd burner.

he's a really meany and sometimes i just want to punch him in the face. he expects huge favors for small ones i give him. i installed $300 worth of programs on his computer just to use his ipod to backup my stuff, and he only backed it up for a day. but i can't say nothing or he won't help me. plus i don't have a lot of money, i wasted like $500 so i have to pay my parents back by not asking for anything.

please do help, thank you

any help, any at all would be appreciated :popcorn:

---

### Post by profeXorGeek on 2007-08-18
I'm not sure if it's possible to actually share a CD/DVD burner from a windows machine to a linux machine. That sounds tricky.

It is possible to share a drive on your linux machine with his windows machine using a program called samba. You can read about configuring samba here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I use an ubuntu machine as a home server with samba shares to my windows machine. I can watch movies, burn files and do lots of other things. Unless the DVD image is a very strange file type it should not corrupt it to burn the disk on the windows machine from the shared folder.

If you can be more specific about what you've tried so far it will give people a better idea of what you have ruled out and how you may be doing it wrong. Good luck!

---

### Post by sarahsilverman on 2007-08-18
> **profeXorGeek said:**
> I'm not sure if it's possible to actually share a CD/DVD burner from a windows machine to a linux machine. That sounds tricky.

It is possible to share a drive on your linux machine with his windows machine using a program called samba. You can read about configuring samba here:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I use an ubuntu machine as a home server with samba shares to my windows machine. I can watch movies, burn files and do lots of other things. Unless the DVD image is a very strange file type it should not corrupt it to burn the disk on the windows machine from the shared folder.

If you can be more specific about what you've tried so far it will give people a better idea of what you have ruled out and how you may be doing it wrong. Good luck!

i connected it to the ip from ubuntu, it opened up a file browser but said it couldn't display any of the files. my goal though is to make use of the burner. is it possible to see files on the ubuntu machine from windows? then using the burning software in windows i can point the file location to the file on ubuntu and burn?

so like i connect the computers. windows can see the ubuntu computer. in the burning software it asks me the location of the file i want to burn. i point it to the file located on the ubuntu machine. and burn. is that possible?

thankyou for being the first to help me :popcorn:

---

### Post by profeXorGeek on 2007-08-18
the way you tried it was wrong for this reason: windows uses an ntfs file system. Linux uses an ext3 file system. Think of it like an English-speaking person trying to read German: windows will not be able to read the files just by connecting to the IP address.

But it IS possible to share files. You just need to install and configure samba. Samba works like a translator...translating files from Linux into the format that windows can read. There are lots of walkthroughs out there and it's a very common task as many people want to be able to see files from their linux machine on ubuntu.

Check out the link that I sent in my previous post. It is a HOWTO for samba (you may also see it spelled smba). If that article doesn't help just try googling something like "Set up Samba on Ubuntu"

Samba shares both ways. You can share a drive from linux to windows and you can mount a drive from windows on linux. What your asking is possible using the samba program!

---

