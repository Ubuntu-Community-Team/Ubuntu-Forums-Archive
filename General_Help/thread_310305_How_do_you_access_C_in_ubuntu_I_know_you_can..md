---
title: "How do you access C: in ubuntu? I know you can."
date: 2006-12-01
forum: General Help
---

### Post by ReconUnit415 on 2006-12-01
](*,) ](*,) ](*,) ](*,) 

I know you can access C: but I dunno how. I have a program installed there.

Please respond.

---

### Post by igknighted on 2006-12-01
It wouldn't be listed as c:, it would be listed by its unix drive designation (for example hda1).  In this case it would probably be in /mnt/hda1.  If it is not, check and see if there is a folder in your / directory called /windows (some distro's do this, dunno if ubuntu is one).  If it is not in either of these, you may need to add it to your fstab file, search the forums, there are many guides for this.

---

### Post by ReconUnit415 on 2006-12-01
> **igknighted said:**
> It wouldn't be listed as c:, it would be listed by its unix drive designation (for example hda1).  In this case it would probably be in /mnt/hda1.  If it is not, check and see if there is a folder in your / directory called /windows (some distro's do this, dunno if ubuntu is one).  If it is not in either of these, you may need to add it to your fstab file, search the forums, there are many guides for this.

I am sorry but I have no dea what you mean. I have a little aexperience with ubuntu but I am still a noobie.

---

### Post by aysiu on 2006-12-01
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) will help you access C:

---

### Post by ReconUnit415 on 2006-12-01
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) will help you access C:

I am talking about  C: virtual dive in linux. this has nothing to do with partitioning. I dont have windows.

I am saying when I install something with wine it shows up that I can put a file into C:.

---

### Post by Cynical on 2006-12-01
well even if he did mount it he wouldn't be able to run the program without wine. Just to clarify, you are talking about a windows application right?

---

### Post by igknighted on 2006-12-01
Oh, sorry, I didnt know you were talking about wine... that should be listed somewhere in wine, not sure where tho

---

### Post by ReconUnit415 on 2006-12-01
> **igknighted said:**
> Oh, sorry, I didnt know you were talking about wine... that should be listed somewhere in wine, not sure where tho

huh. I just really want to get Anarchy Online :) (and a whole tone of other programs) but it is already installed and it wont let me install it aagin in a different directory or not. now I'll never install it without help.

---

### Post by rajasekhar.yeruva on 2006-12-01
It is the Wine Directory in your Home folder itself. 

/home/Username/wine

and your program will be Under Wine program files like the ancient windows style.

/home/username/wine/program files/App Dir you are looking for

---

### Post by aysiu on 2006-12-01
Don't forget the dot in there:
/home/*username*/.wine/drive_c/Program Files/Application Name

More details here:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by ReconUnit415 on 2006-12-01
Wine doesn't exist in my home/username folder

---

### Post by aysiu on 2006-12-01
> **ReconUnit415 said:**
> Wine doesn't exist in my home/username folder
It's a hidden folder. If you're using Ubuntu or Xubuntu, press Control-H.

If you're using Kubuntu, press Alt-V, then H.

---

### Post by ReconUnit415 on 2006-12-01
> **aysiu said:**
> Don't forget the dot in there:
/home/*username*/.wine/drive_c/Program Files/Application Name

More details here:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

Ok I know how to get to that but what I need to know is how to access C:\program files\.....

---

### Post by aysiu on 2006-12-01
> **ReconUnit415 said:**
> Ok I know how to get to that but what I need to know is how to access C:\program files\.....
And I'm telling you.

It's /home/*username*/.wine/drive_c

That's what C:\ is when you're using Wine.

C:\Program Files **is** /home/*username*/.wine/drive_c/Program Files

---

### Post by ReconUnit415 on 2006-12-01
> **aysiu said:**
> And I'm telling you.

It's /home/*username*/.wine/drive_c

That's what C:\ is when you're using Wine.

C:\Program Files **is** /home/*username*/.wine/drive_c/Program Files

 Gd, sorry If I was getting a little annoying there but now.....

On Anarchy Online:
"An Installation Support file could not be installed. (0x8000ffff)"

Don't worry you dont have to help me on this one. I know you probably cant figure this out.

---

### Post by aysiu on 2006-12-01
> **ReconUnit415 said:**
> Gd, sorry If I was getting a little annoying there but now.....

On Anarchy Online:
"An Installation Support file could not be installed. (0x8000ffff)"

Don't worry you dont have to help me on this one. I know you probably cant figure this out.
You're right. I probably can't help you there, but I've generally found [Google searches on errors](http://www.google.com/search?hl=en&q=An+Installation+Support+file+could+not+be+installed.+%280x8000ffff%29&btnG=Google+Search) can sometimes help.

---

