---
title: "Making vlc the default app"
date: 2005-04-04
forum: General Help
---

### Post by timothy82 on 2005-04-04
Hi,

I've got trouble making vlc my default application for viedo files (avi, mpg etc).
Whenever I try to do that (right click on file - Properties - Open With - Add - selecting vlc - Add), I get the following message:

**Could not add application to the application database.**

Does anyone have a hint on how to solve this? Is there another way of making an application the default for a certain file type?

Tim

---

### Post by Leif on 2005-04-04
Try right-click - Open with - Open with Other application, and choose vlc there. See if that does it.

---

### Post by timothy82 on 2005-04-04
Nope, exactly the same thing happens. What is this "application database" anyway?

---

### Post by Leif on 2005-04-05
Sorry, this has me beat, as what I said works for me.

---

### Post by condorloco on 2005-04-05
I have exactly the same problem. Has anyone any idea?

---

### Post by keffo on 2005-04-05
Hm, first of all.. if there is no VLC in list.. just type vlc (as command)

it works for me..

second, check that you have rights etc to the file you try to change
def. app on.. if you aint got the rights, this 'bug' appears.


this is how I sovled it

---

### Post by timothy82 on 2005-04-05
[QUOTE=keffo]if there is no VLC in list.. just type vlc (as command)[/QUOTE]

vlc does show up in the list of applications and I can select it just fine, but I'll always get that error message. I've tried with other video players (xine), and there is no problem.

I just figured out that if you select vlc in the list of applications, then click on "Use custom command" and replace "wxvlc" with simply "vlc", the problem is resolved. Now vlc is the default player of choice.

Thanks for the hint,

Tim

---

### Post by feloc on 2005-09-27
I have this same problem with Mplayer.

Right-Click -> Properties -> Open With -> Mplayer

=  Could not add application to the application database.

Right-Click -> Open with other application -> Mplayer

=  Could not add application to the application database.

When I play the video in terminal mplayer (and the video) works just fine. I had Totem as a default .mpg player before, I removed it recently and now got this problem. What to do?

When I try to do the same thing with VLC, I get the same error...

---

### Post by mcduck on 2005-09-27
I had that problem also, and then I found out that .local in my home folder was owned by root so I didn't have rights to modify it (and default app settings are there). Check that out, and if it really is owned by some other than yourself just delete the folder and it will be created again, now with proper owner and rights. After that everything should work again.

---

### Post by wcbaker on 2005-10-07
I tried that and I am getting the error message that feloc got: "Could not add application to the application database." when I try using VLC. Has anyone else fixed this problem?

---

### Post by Trajan on 2005-10-10
I got mine to work after changing  the "wxvlc" in " Use a custom command" in the Open With dialogue. For some reason wxvlc is the default command and thats why it cannot be found in the DB... just type in the correct "vlc" and it should open correctly.

---

### Post by spin2cool on 2007-01-13
Late to the party here, but for other people who find this thread, the solution is simple.  you need to claim ownership of your ~/.local folder.

So, at the command prompt:
```

sudo chown -R <username> ~/.local

```

Should solve the problem.

---

### Post by xavim on 2007-01-16
The following command will set both the right owner *and* the right group for the folder:
```
sudo chown -R <username>.<username> ~/.local
```
Note: In my case, I found that the culprit was Google Earth.  I installed the application and it created my *~/.local[I] using [I]root* as owner.

---

