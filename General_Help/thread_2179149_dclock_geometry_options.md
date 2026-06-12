---
title: "dclock geometry options"
date: 2013-10-06
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-10-06
Anybody here been able to get dclock to honor it's geometry options? The man page is absurdly vague about the syntax. Usually I solve that problem by Startpaging (sorta like googling, without the evil) the program name and "examples" but no joy in this case. I did find some examples of use of the geomenty options but they were inconsistent (which is a virtue if it means the program isn't picky) and more importantly, none of them worked for me. For me, in Lubuntu 13.04, 32 bit, dclock starts maximised no matter what I tell it. I've tried invoking in a script following the dclock command with wmcntrl commands but the script opens dclock, which seems to work normally, but never moves on to issue the wmcntrl commands. So I tried using a master script to call another script containing the dclock command and THEN issue the wmctrl commands as the next step in the master script but IT hung after the other script started dclock. Is dclock somehow stunning bash into catalepsy or what? Dclock WILL resopond to wmctrl commands though, if I issue them ftom lxterminal. I have to issue a toggle mode command and then it will respond to the size/position command. For anyone not familiar with Lubuntu, I should point out I'm using Openbox as a window manager.  Any ideas would be appreciated.

---

### Post by vasa1 on 2013-10-06
Your views on Google, man, and catalepsy aside, you haven't said anything about **lubuntu-rc.xml** ;) Did you try that? From your post, it isn't clear what you've tried. So far, I've not found the need to install **wmctrl** in Lubuntu 13.04.

If you reveal the contents of the scripts you mention and when exactly you invoke them, the experts here may be able to help. I don't have dclock installed. The default simple digital clock that can be added via lxpanel is sufficient for my needs.

---

### Post by stinkeye on 2013-10-06
What you can do is start dclock and resize and position the window where you want it, 
then in a terminal run **xwininfo**.

Select your  dclock window and the last line of output will show the geometry.
Copy that line to use with dclock.

May also be a window manager thing as just running "dclock" 
always starts a small window in compiz.

---

### Post by vasa1 on 2013-10-06
@stinkeye, OP is using Lubuntu 13.04 and there's no compiz by default but who knows what we add/subtract over time.

I've installed dclock after seeing your post and it **didn't open maximized**. I saw a window similar to the one you've posted. My "prejudice" is that OP has done "something" and there's not enough data made available to troubleshoot :D 

I get the same error in the terminal: "Warning: Cannot convert string "**helvetica-medium-r-normal--14*" to type FontStruct*".

Also, I couldn't find mention of the program on the original author's [website]("http://opencircuitdesign.com/~tim/programs/") :(

---

### Post by vasa1 on 2013-10-06
I used the information provided by **xwininfo** as suggested by stinkeye. Then, I edited lubuntu-rc.xml to include:
```
    <!-- Launch dclock -->
    <keybind key="C-S-d">
      <action name="Execute">
        <command>dclock -geometry 577x194+119+139</command>
      </action>
    </keybind>

```
just above **</keyboard>**. After running **openbox --reconfigure**, dclock opens with the prescribed geometry.

No scripts needed. No recourse to wmctrl.

---

### Post by Dreamer Fithp Apprentice on 2013-10-07
> **vasa1 said:**
> . . .  you haven't said anything about **lubuntu-rc.xml** ;) Did you try that?No. It didn't occur to me that it might override explicit geomety options in a command. I assumed it was the other way around. But, I experimented and, indeed, settings in lubuntu-rc.xml will make geometry options contrary to them completely ineffective, at least in the case of this program, and I'd assume, generally. And that was the problem. That's probably just about the last thing I'd have thought to try and it was the FIRST thing you mentioned. I'm impressed. Thanks much, Vasa1.

> **stinkeye said:**
>  . . . then in a terminal run **xwininfo**Thank you,  Stinkeye. That's a nice command and I didn't know about it. I've just  been guestimating based on my screen resolution and correcting if it  didn't look quite right. I'll get a lot of use out of it.

==========
Added after posting by edit:

I was interrupted several times while composing the above and when I finally got to post it, I see you've posted again, Vasa1. Thanks for the example. I'll just use the dclock options because I might use dclock for something else and want another size sometime. I'll be much more conservative in my lubuntu-rc.xml statements in the future, making them as narrow as possible, since they are apparently harder to override than I realized. Thanks, again.

---

