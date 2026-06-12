---
title: "Stuck in blank white screen!"
date: 2008-02-28
forum: General Help
---

### Post by bobbo85 on 2008-02-28
I am about a month into using Ubuntu and loving it!

However, today I was surprised when I hit "log out" to switch to another user, and the screen turned white!  Nothing but a mouse pointer remained...

Question:  How can I get my GUI back up and running without restarting the computer?


Story:
Steps taken:
1)  Originally I had 1 user.  I decided to make a new user to play with desktop appearance/setup
2)  While listening to music and chatting on pidgin, I chose "switch user"- not log off.  I was surprised to find that even after logging into the other new user, I still heard the music from user1, as well as the new IM sound from user1... 
3)  After playing with the settings for user2 for a while, I hit "log off"
White screen...  but still music, still a mouse pointer...

What I tried (and how I failed):
I hit all kinds of combinations of buttons blindly, and came upon the ctrl alt f1combo that brought up a terminal. 
Question - How can i get back to my GUI once I'm in this terminal?  I logged in, but I don't know any commands to start the GUI.  I tried "Help" and "man man" to try and find a list of commands... but none of them said anything about getting back to the GUI.

Hitting ctrl+alt+ f1... up to f6 did the same thing, another login in the CLI.  f7 brought up the white screen again with the mouse pointer.  i think f10 brought up a blank CLI, and when I tried f9 from there it gave me a bunch of "Test... OK" messages.

I finally got back to a GUI without having to turn off the computer by trying ctrl+alt+backspace (I think that was it) - but this restarted the computer!  

Thanks in advance everyone.

---

### Post by Yellow Pasque on 2008-02-28
> Question: How can I get my GUI back up and running without restarting the computer?
....
> Hitting ctrl+alt+f7 brought up the white screen again with the mouse pointer.

You probably won't be able to get the GUI back without at least restarting X (killall xorg; startx)

---

### Post by kesman on 2008-02-28
Killing xorg is not the best option you have. Try this instead, it shuts gdm and xorg down more appropriate way:
```

sudo /etc/init.d/gdm restart

```

---

### Post by bobbo85 on 2008-02-29
> **kesman said:**
> Killing xorg is not the best option you have. Try this instead, it shuts gdm and xorg down more appropriate way:
```

sudo /etc/init.d/gdm restart

```

How did you know that command?  And how did you know which file needed to be restarted?  Thanks for the quick response by the way!

---

### Post by joebeasley on 2008-03-01
Type in the password of the user you are switching to and hit enter.

---

