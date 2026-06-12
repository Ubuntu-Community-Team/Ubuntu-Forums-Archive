---
title: "Active X"
date: 2007-03-02
forum: General Help
---

### Post by CheeseQueen452 on 2007-03-02
I would like to watch the tv shows at in2tv.aol.com, but it needs active x. Is there anything I can do? Is there a way to get it, or an extension that'll allow the videos to play? HELP!

---

### Post by jimbob on 2007-03-02
When I went there it said I had to have active-x plugin for mozilla and did I want to install it.

I said yes and it did and now the videos play just fine

Is that what you did?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-02
I tried that, but it wouldn't install. Now what?

> **jimbob said:**
> When I went there it said I had to have active-x plugin for mozilla and did I want to install it.

I said yes and it did and now the videos play just fine

Is that what you did?

---

### Post by jimbob on 2007-03-02
What do you mean it wouldn't install?   What message(s) did you get?

What do you get when you type about:plugins in your browser window?  Post the screen shot so I can compare it with mine - I don't know what that plugin is called exactly.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-02
Here's some screenshots:
[http://img.photobucket.com/albums/v209/Sasafrass/Screenshot.png](http://img.photobucket.com/albums/v209/Sasafrass/Screenshot.png)
[http://img.photobucket.com/albums/v209/Sasafrass/Screenshot-1.png](http://img.photobucket.com/albums/v209/Sasafrass/Screenshot-1.png)
[http://img.photobucket.com/albums/v209/Sasafrass/Screenshot-2.png](http://img.photobucket.com/albums/v209/Sasafrass/Screenshot-2.png)

I don't see active x in about: plugins.

> **jimbob said:**
> What do you mean it wouldn't install?   What message(s) did you get?

What do you get when you type about:plugins in your browser window?  Post the screen shot so I can compare it with mine - I don't know what that plugin is called exactly.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-03-03
Sorry, I meant to post the screenshot of your plugins so I could see where ours differ.  Mine is attached ( in 3 sections ).

I am running Feisty Fawn 7.04 and Firefox 2.0 which may make a difference.  I also have Flash 9 installed.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-03-03
Let's see if I can get all 3 of them this time ...

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by disco on 2007-03-03
I'm having this same problem. Is a solution even possible? The Mozilla Active-X control plugin only goes up to version 1.5 of firefox, according to the site.

I got that exact same error message yesterday, and assumed that it was due to trying to add a FireFox 1.5 plugin to FireFox 2.0

---

### Post by jimbob on 2007-03-03
Well, here is a real puzzler for you.  I booted up my Edgy installation which I haven't used for a few weeks.  When the  in2tv site opened it said that I needed to install the Flash plugin so I clicked on install and it did the install without any problem.

Then I clicked on one of the videos to play and it played it just fine without even ASKING for anything to do with active-x.

Go figure!!

---

### Post by CheeseQueen452 on 2007-03-03
Well, I compared your plugins with mine, & I noticed that I didn't have the totem plugin. So, I installed that but still no luck.

> **jimbob said:**
> Let's see if I can get all 3 of them this time ...

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-03
Did you try playing a video that's NOT on the main page? For instance, I wanted to watch Perfect Strangers(very funny). It's in the comedy section. Try that & see if you can play it. I really don't know why it doesn't work for me, other than not having active x. It just won't install for some reason.

> **jimbob said:**
> Well, here is a real puzzler for you.  I booted up my Edgy installation which I haven't used for a few weeks.  When the  in2tv site opened it said that I needed to install the Flash plugin so I clicked on install and it did the install without any problem.

Then I clicked on one of the videos to play and it played it just fine without even ASKING for anything to do with active-x.

Go figure!!

---

### Post by jimbob on 2007-03-03
Can you play flash videos from youtube and others OK?  If I get a chance I'll try my Dapper installation later and see what that does.

Which distro are you running?

---

### Post by CheeseQueen452 on 2007-03-03
Yep, I can play the videos at youtube. I even have an account there. I'm running edgy.

> **jimbob said:**
> Can you play flash videos from youtube and others OK?  If I get a chance I'll try my Dapper installation later and see what that does.

Which distro are you running?

---

### Post by jimbob on 2007-03-03
Yes, you're right, it asks for the active-x plugin in the comedy section.  It looks like it is trying to install a .dll file and is failing for some reason.

I suggest to you that aol in their infinite and narrow-minded wisdom is trying to install into some C:\windows\... directory that doesn't exist on Linux.

Most of ours are in /use/lib/codecs/*.dll - if you could get a hold of it and stick it in there it might work but it is probably more involved than that.

Maybe someone else who has it wojking will pick up this thread.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-04
Well, if someone has any words of wisdom on this, I'd appreciate it!

---

### Post by jimbob on 2007-03-04
Good news (I think).  I got Perfect Strangers Ep 1 to play.  Here's what I did:

Downloaded the add-on User Agent Switcher.
Made sure it was set to Windows IE 6 before I brought up the web page for in2tv
Tried to play the featured video of Joey and it said I had to have Macromedia Flash installed to play.
I knew I already had it but I said OK to install and it took me to the Macromedia page.
Decided I didn't want to download it so I just closed the window.
Went down the page to Perfect Strangers and selected Ep #1 to play and it played!
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-04
I tried that extension & it didn't work. Still wants active x. Now what?

> **jimbob said:**
> Good news (I think).  I got Perfect Strangers Ep 1 to play.  Here's what I did:

Downloaded the add-on User Agent Switcher.
Made sure it was set to Windows IE 6 before I brought up the web page for in2tv
Tried to play the featured video of Joey and it said I had to have Macromedia Flash installed to play.
I knew I already had it but I said OK to install and it took me to the Macromedia page.
Decided I didn't want to download it so I just closed the window.
Went down the page to Perfect Strangers and selected Ep #1 to play and it played!
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-03-04
It sounds like your User Agent Switcher isn't working right.  You want to make it think it is talking to W$ XP instead of Linux and it stops asking for active-x (at least for me).  If you can get by that you will be asked to download Flash and I was able to fake it out from there.  By the way, when you get it to work for the first one it will continue to play any and all you want as long as you don't leave the web site.

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by CheeseQueen452 on 2007-03-04
I set the User Agent Switcher to IE, but no luck. I do have flash installed. I wish there was a way....

> **jimbob said:**
> It sounds like your User Agent Switcher isn't working right.  You want to make it think it is talking to W$ XP instead of Linux and it stops asking for active-x (at least for me).  If you can get by that you will be asked to download Flash and I was able to fake it out from there.  By the way, when you get it to work for the first one it will continue to play any and all you want as long as you don't leave the web site.

---

### Post by CheeseQueen452 on 2007-03-20
Can anyone help?

---

