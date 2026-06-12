---
title: "Deleted user account"
date: 2013-09-26
forum: General Help
---

### Post by The musmula on 2013-09-26
MY SISTER IS GOING TO KILL ME! I need to calm down, I`ve got a heart attack, when I found out what I did... 2 seconds ago...

a few days ago I have created a account for my sister on my ubuntu 13.04, 40GB of her stuff I have placed there, she told me then that she doesen`t want that account, i deleted it, but I have forgotten that I pressed delete files when asked, SHE TOLD ME THAT SHE DOESEN`T WANT HER FILES STORED ON MY PC! She said that something will go wrong, AND IT DID. That personal stuff is HIGHLY important for her, I need to get it back. She is in town right now and she is going to rip my skin of my flesh if she finds out what happend, I need to restore those files so we can burn them onto DVDs, PLEASE I NEEEED HELP [-o<

Is there ANY way to get it back so that it looks like the same as it was?

---

### Post by philinux on 2013-09-26
> **The musmula said:**
> MY SISTER IS GOING TO KILL ME! I need to calm down, I`ve got a heart attack, when I found out what I did... 2 seconds ago...

a few days ago I have created a account for my sister on my ubuntu 13.04, 40GB of her stuff I have placed there, she told me then that she doesen`t want that account, i deleted it, but I have forgotten that I pressed delete files when asked, SHE TOLD ME THAT SHE DOESEN`T WANT HER FILES STORED ON MY PC! She said that something will go wrong, AND IT DID. That personal stuff is HIGHLY important for her, I need to get it back. She is in town right now and she is going to rip my skin of my flesh if she finds out what happend, I need to restore those files so we can burn them onto DVDs, PLEASE I NEEEED HELP [-o<

Is there ANY way to get it back so that it looks like the same as it was?

Just check that the users home directory is still there. Normally removing a user does not remove the users home folder.

Open files click on computer and then home to see if it's still there.

---

### Post by Petro Dawg on 2013-09-26
I've never tried to recover deleted files before, but I know there is software out there that can do it.  First off, I would immediately boot from a live CD to keep from over writing the deleted files on the hard drive.  Next I would go through the links below to see what suggestions may work for you.[URL="http://askubuntu.com/questions/3883/how-to-recover-deleted-files"]

http://askubuntu.com/questions/3883/how-to-recover-deleted-files[/URL][URL="https://help.ubuntu.com/community/DataRecovery"]

https://help.ubuntu.com/community/DataRecovery[/URL]

Good Luck.

---

### Post by The musmula on 2013-09-26
the home folder is deleted
and I am trying to use photorec to recover them, but the end results will be a bunch of files with a random name and I am not sure if those were  in it or not, I need something that will recover it whitout making that what photorec makes

---

### Post by Impavidus on 2013-09-26
You copied 40GB of data there only a few days ago. Where did the data come from? Is it still there?

---

### Post by The musmula on 2013-09-26
it came from an other pc and there they were deleted too

---

### Post by slickymaster on 2013-09-26
If you're not willing to use Photorec, there's same other choices for you to use. See this: [HOW TO RECOVER DELETED FILES IN UBUNTU / DEBIAN WITH SCAPEL AND FOREMOST]("http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html")

---

### Post by The musmula on 2013-09-26
I will get the same result, but now I am finished with photorec and I need to reorganize the files now, it should take a few days, there are 150000 files to organize :(
thank you all for your support, altought it didn`t solve my problem

---

### Post by philinux on 2013-09-26
> **The musmula said:**
> I will get the same result, but now I am finished with photorec and I need to reorganize the files now, it should take a few days, there are 150000 files to organize :(
thank you all for your support, altought it didn`t solve my problem

I deleted a load of mp3 files and used photorec to recover them. I then used a command line renaming tool that looked in the files and used the info to rename the mp3's back to a recognisable form.

I'm trying to remember the tool or app. It was a while ago.

[edit] it was an app called eyed3 and it's in synaptic. It can look inside mp3's and read the id3 tags and you can then use the info to rename the file.

[http://www.linuxquestions.org/questions/linux-general-1/bash-script-for-sorting-and-renaming-multiple-mp3-files-by-id3-tags-602105/#post4775741](http://www.linuxquestions.org/questions/linux-general-1/bash-script-for-sorting-and-renaming-multiple-mp3-files-by-id3-tags-602105/#post4775741)

not sure how to sort through 150000 files and id mp3's though. Someone else may know.

---

### Post by The musmula on 2013-09-27
OK, I have used photorec and it recoverd about 100GB files, and my whole home folder is in a really bad shape, so I have seperated useful from unuseful. I have filtered the folders for pdf, odt, doc, xls,... after filtering for png, I have got a huge number of results, normally cutting that to another folder wouldn`t be a problem but since my home folder sucks, I need a way to cut that to the other folder without nautilus (since it has a lot of visual fx) (so using the terminal) but without killing my PC, has anybody a idea?

---

### Post by The musmula on 2013-09-29
ok, I used the gnome (no effects) shell for filtering the jpg`s, and I have cutted the big folder into 6 small ones, so it is going well so far, I haven`t been able to recover the most important but, well, it IS my fault

---

