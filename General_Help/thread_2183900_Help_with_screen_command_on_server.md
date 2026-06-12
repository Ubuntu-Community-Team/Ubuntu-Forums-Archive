---
title: "Help with screen command on server"
date: 2013-10-26
forum: General Help
---

### Post by Elochai on 2013-10-26
I like to say sorry if this seems like a very noob question but I don't have much experience with screen or other commands that allow me programs after I log out of a session.

So here the deal. I am renting a server for hosting game servers on. I am currently running one Killing Floor server on it right now.


So when I logged out of SSH or x2go the game server would also shutdown as the program would get terminated along with my session.


I remember something about this with my ND gaming server a few years back and sure enough I found the command I used to fix this issue, which was screen.


So I created a .sh file to run the Killing Floor server with screen.


```
#!/bin/sh
echo "Starting Killing Floor Server"
sleep 1
screen -A -m -d -S KFserver ./ucc-bin server KFO-FrightYard.rom?game=KFStoryGame.KFStoryGameInfo?VACSecured=true?MaxPlayers=6?AdminName=Elochai?AdminPassword=XXXXX -nohomedir 
```

Open SSH and ran it, the screen cleared but the Killing Floor server did show up in game and the administration web panel is working. So everything is fine, but one part.

When I logged back into the server, I want to bring up the Killing Floor shell to read the live data and to be able to input commands.

I can't find it anywhere, even doing screen -ls I see 2 sessions but I can't access them. Maybe I am doing it wrong. Server is still running tho. But this will be very bad when I do another game server that can only have commands inputted by the shell.

---

### Post by Lars Noodén on 2013-10-27
Usually you reattach to a screen session using -x or -d -r.  So if you wanted to attach to session "KFserver" you could do it something like this:

```

screen -d -r -S KFserver

```

That will detach the pre-existing session and take it over. 

Have you looked at tmux yet?  Some find it simpler and easier to use.  If you're just getting started, I would recommend looking at it first.

---

### Post by Elochai on 2013-10-27
> **Lars Noodén said:**
> Usually you reattach to a screen session using -x or -d -r.  So if you wanted to attach to session "KFserver" you could do it something like this:

```

screen -d -r -S KFserver

```

That will detach the pre-existing session and take it over. 

Have you looked at tmux yet?  Some find it simpler and easier to use.  If you're just getting started, I would recommend looking at it first.

I tried bring it back with no luck at first. It wasn't listed at all in the screen -list.

But it was in fact running. Very odd, anyway I had to do a reboot for some updates and when I started the server back up and used screen again, it now listed itself on the screen -list. So I am able to access it now using screen -x and screen -d -r -S but I got to use the PID numbers instead of the name.

So all is well.

---

