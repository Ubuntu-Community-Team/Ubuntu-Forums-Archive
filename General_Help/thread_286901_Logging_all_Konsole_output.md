---
title: "Logging all Konsole output"
date: 2006-10-28
forum: General Help
---

### Post by bleearg on 2006-10-28
Is there any way to automatically log my screen output when a Konsole or Terminal session is opened?  In Windows, I use SecureCRT to log all my SSH and telnet sessions.  I'm looking for similar functionality in Konsole, since I obviously use it for the same purpose.  I often have to go back and look at logs in case I flub something up or have to post notes in a trouble ticket.

I do know that Konsole can log the history, but it's not automatic and doesn't log to a file, from what I can tell.  Is it possible to do this using 'screen' and some type of bash script?

I'd appreciate any advice, as long as it's not "use PuTTY" or "install SecureCRT using wine".  Done them both...absolutely abhor PuTTY and don't like using wine.

thanks in advance,
evt

---

### Post by reison on 2007-03-15
I'm looking for the same thing, but using gnome-terminal. 

The ONLY thing I've turned up so far is an app called [Terminator]("http://software.jessies.org/terminator/"), but I've found it to be a little buggy, in particular where it returns the cursor after displaying many lines.

I'd think there's some way to pipe output to a file with a time and date stamp, like putty and SecureCRT do, native to Linux, but I can't find it...

---

### Post by bleearg on 2007-03-15
I've been looking at using Screen for this, because that seems to be the way to go.  I'm just having difficulty figuring out how to automatically start a screen session every time I open up Konsole.  I know there's a way to open screen by going to the Konsole menu, but again, that's annoying.

---

### Post by reison on 2007-03-15
I happened upon [[COLOR="SeaGreen"]this site[/COLOR]]("http://www.builderau.com.au/program/linux/soa/Using_script_to_record_terminal_sessions/0,339028299,339273932,00.htm") that suggests using **script** to do it. I tried it myself and it works pretty well, but as you wrote, there's the matter of it happening automatically.

Script is pretty handy, though.

---

