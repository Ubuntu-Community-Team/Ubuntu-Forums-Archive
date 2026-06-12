---
title: "Screen while booting"
date: 2008-03-18
forum: General Help
---

### Post by alejandro.mc on 2008-03-18
So, here's the thing, After the GDM appears and I write my user account and my password, Ubuntu takes about 10 seconds to load. Nothing wrong with that, but while waiting those ten seconds I have to view this orange screen. I would like it to be black or any other color, but not that awful orange/pink colour it has, that doesn't combine at all with what loads after those 10 seconds, meaning my desktop and my theme and everything. 

I have advanced desktop effects enabled, using a cube.

I've already tried changing the colour from the Desktop Cube options in Advanced Desktop Effects Settings, the colour of the desktop in the Appearence Windows to Change Background, and changing the background colour from the Login Windows Options.

Any ideas?

Thanks in advance.

Alejandro

---

### Post by tlink on 2008-03-18
Yeah, it does that no matter if you're running compiz or not... 

Wish I knew how to change this also

---

### Post by mk1w86 on 2008-03-18
Goto  
System >> Administration >> Login Window >> click Local tab >> Background colour, then just choose the colour you want.

---

### Post by alejandro.mc on 2008-03-21
Thanks but I tried already that. Still can't fix this.. Anyone else?

---

### Post by NightwishFan on 2008-03-21
As far as I know this is fixed in Hardy, I am pretty sure there is a way to fix in Gutsy. Try the search function.

---

### Post by Mustard on 2008-03-21
> **alejandro.mc said:**
> Thanks but I tried already that. Still can't fix this.. Anyone else?

I have read a thread with a fix for this.  It's in one of the many threads discussing gnome loading very slowly after the gdm login. I tried a quick search with no luck, but it took quite a bit of reading before I stumbled across it last time.

---

### Post by alejandro.mc on 2008-03-21
Hey thanks to everyone for replying, yep I'll keep looking of course, that's how we Ubuntu users usually proceed! Never give up =)

I'll keep searching till i come across that post you mentioned, and then will copy this link here, there has to be a lot more of users wanting to modify that.

THX

---

### Post by Mustard on 2008-03-22
> **alejandro.mc said:**
> Hey thanks to everyone for replying, yep I'll keep looking of course, that's how we Ubuntu users usually proceed! Never give up =)

I'll keep searching till i come across that post you mentioned, and then will copy this link here, there has to be a lot more of users wanting to modify that.

THX
Most seemed more worried about the time gap between gdm login and the screen appearing.  The brown screen was killing my black theme though, so I was very pleased to see someone post a fix. :)

---

### Post by alejandro.mc on 2008-03-22
Have not found it yet.. i'll keep looking though..

Bye!

---

### Post by ryanhaigh on 2008-03-22
I know that there is a file somewhere in /etc/gdm that causes this, I just can't remember exactly which

Found it in an old thread:
> 
Based on what I've read, it seems like commenting the following lines out in "/etc/gdm/PreSession/Default" seems to solve the problem and the color then the color should be left at whatever color is set as the login screen background until the desktop loads.


# Default value
#if [ "x$BACKCOLOR" = "x" ]; then
# BACKCOLOR="#dab082"
#fi

#"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"

or this which I prefer
[quote]
It&#8217;s a bug in 7.10, so you have to do it this way:

Open the file /etc/gdm/PreSession/Default in a text editor with administrator privileges (e.g. sudo vim /etc/gdm/PreSession/Default) and search for the part that says

# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=(some color in hex)
fi

and change it to:

# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=&#8221;x&#8221;
fi


[/quote]

---

### Post by alejandro.mc on 2008-03-23
I have to be really sure, are you really sure this it's not going to corrupt my login in any way, I'd hate to reinstall and set up all Ubuntu again..

I'm thankful for the information, but is this safe? Please let me know and I shall try it.

Thanks very much!

---

### Post by ryanhaigh on 2008-03-23
On the machine I am using now I have:
# Default value
#if [ "x$BACKCOLOR" = "x" ]; then
# BACKCOLOR="#dab082"
#fi
and it boots fine.

---

### Post by alejandro.mc on 2008-03-27
Hey ryanhaigh I want to thank you very much for your reply, it worked like a charm. It's incredibly comforting to see the black screen while the destop boots, once again thanks for your effort and concern!

Good luck!

---

