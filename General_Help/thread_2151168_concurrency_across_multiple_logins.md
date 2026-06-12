---
title: "concurrency across multiple logins"
date: 2013-06-03
forum: General Help
---

### Post by planarian on 2013-06-03
I need to have two logins/terminals on my machine running simultaneously, but I've noticed that whenever I switch between them, processes in the inactive terminal seem to stop. How do I prevent this from happening?

---

### Post by 25tom on 2013-06-03
I presume you mean between say, 'Ctrl-Alt-F1' and 'Ctrl-Alt-F2' ttys? If you have X, my quick fix would be to use that instead with two terminal emulator windows, or even use the 'terminator' terminal which allows for multiple terminal panes so you can run two terminals easily side-by-side in the same window.

Hope this helps :)

---

### Post by Lars Noodén on 2013-06-03
I haven't run into what you are describing.  How are you running the terminals and precisely what steps make them stop?

---

### Post by planarian on 2013-06-03
@25tom: Thanks, I'll look into "terminator." 

@Lars: If I start an mp3 playing, or a Youtube video and then toggle to a different terminal with ctrl-alt, and then return to the first terminal (where X is running), it continues from the exact point I left it. This is only a test case. My goal is to have two different accounts running on (I believe) two separate xservers using gdmflexiserver. As I use one of these for browsing, the other will be streaming data.

---

### Post by 25tom on 2013-06-03
Ah, if you're using X within the terminals, terminator may not be much use as it deals only with the command line (as far as I know). Unless you're doing this purely out of interest, or really need to use separate logins/X servers, it might be better just to use different workspaces rather than different terminals? Ctrl-Alt-arrow keys usually switch between workspaces. Otherwise I don't know of any way to have two different accounts' logins going at once...

---

### Post by planarian on 2013-06-03
For security reasons I need separate logins. But given Linux's multi-user heritage, I don't understand why this should be problem....

---

### Post by 25tom on 2013-06-03
If you can use the command line for one of the logins you could do whatever for login A and then open a terminal emulator and type "su *whatever-the-other-username-is*" (without quotes) to log in as the other user in the terminal - it being done within the X login for user A, though, I don't know how that would affect your security issues...

Ideas, anyone else...?

---

### Post by Lars Noodén on 2013-06-04
I've experienced the same thing, I think that is the way that X works and don't know a way around it.  If I have something streaming or playing in the X server and I switch to a console with ctrl-alt-f1 or something like that, the activities in X get put on hold.  Now if you open a terminal with ctrl-alt-t in the X server, the player will keep going, but I think that's not what you're after.

---

### Post by planarian on 2013-06-04
It turns out that if I make both of the accounts members of the "audio" group, the mp3-player issue goes away. I also finally got a chance to test the streaming facility (TDAmeritrade) and it seems to work fine when I switch terminals, so perhaps the problem was narrower than I'd assumed. Thanks, everyone.

---

