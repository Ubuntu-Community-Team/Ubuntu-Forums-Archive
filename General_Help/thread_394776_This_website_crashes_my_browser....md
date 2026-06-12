---
title: "This website crashes my browser..."
date: 2007-03-27
forum: General Help
---

### Post by frychiko on 2007-03-27
It'd probably crash your browser too. 

[http://www.brandeli.com/default.asp]("http://www.brandeli.com/default.asp")

Does it crash for you? It won't crash straightaway you have to click a few menu items and go back to the main menu/homepage a few times.

Anyone know how I can fix it? I was thinking it was a flash problem.. (It crashes with Firefox and Opera) but trying some fixes hasn't helped...
I'm using Fiesty Beta with the latest upgrades.

cheers!

---

### Post by chewearn on 2007-03-27
Yup.  Crashed my Firefox :( 

Worked for Firefox in Windows though, sort of.  The Japanese characters become squares, but no crash.

---

### Post by IcemanV9 on 2007-03-27
It crashed mine (Firefox) as well. Looks like it was a bad design. I could see a few "undefined [Japanese characters gone crazy]" on the home page. I believe that's what caused it to crash. You can send the problem report to its webmaster.

---

### Post by oracle5 on 2007-03-27
It didn't crash firefox for me but I also have no script making sure scripts that I may not want to run don't run.

oracle5

---

### Post by Arisna on 2007-03-27
It didn't crash Konqueror for me just now, but I was able to get this message from a coding error console:

```
Error: http://www.brandeli.com/lib.js: SyntaxError: Parse error at line 155
```

To be fair, though, lots of sites, including the post page I'm on right now, contain coding errors according to Konqueror, and they don't crash Firefox.

---

### Post by frychiko on 2007-03-27
Normally I wouldn't care... but it's a site my GF uses alot and she's getting annoyed.. 

"You can send the problem report to its webmaster."

Good idea! That's one idea I will try out...

---

### Post by Tim___ on 2007-04-12
It does not crash for me. 

I'm using stock firefox on feisty if that makes a difference. :)

---

### Post by DeathOnJuice on 2007-04-12
Does the website have any text boxes with large amounts of text in them? I'm talking about something like this but with a lot of text:

```
Ello, poppet
More text for scrollbar
More text
More
```

Also, could you give me the version of your nvidia-glx package if you use it?

If your nvidia-glx version is 8545 or 8778 (those might not be exactly right, but I know it starts with 8), open up the terminal and do a sudo gedit /etc/X11/xorg.conf, then go to the section called Device. It should look like this:

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
```

Now, add this line (but don't change the lines already there):

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "RenderAccel" "false"
EndSection
```

Then, restart your computer. If this is the problem I'm thinking of, that should fix it.

EDIT: Actually, I think yours is a different problem. The one I'm thinking of would boot you back to the login screen. Still, this might be it, so try it.

---

### Post by JensenDied on 2007-04-12
well, doesn't crash here, also running no-script, have not tried with it off yet, but according to firebug there is some japenese characters in the javascript, most are in comments, but this part might be whats causing the issues.

```

function httpObjGenerateFail(){
 alert('&#12372;&#21033;&#29992;&#12398;&#12502;&#12521;&#12454;&#12470;&#12540;&#12391;&#12399;&#12289;&#24403;&#12469;&#12452;&#12488;&#12434;&#12372;&#21033;&#29992;&#38914;&#12369;&#12414;&#12379;&#12435;&#12290;');
 return false;
}

```

I'll see if disabeling no-script crashes on the page then now.
Edit: 
Nope, nothing. Don't necessarily see any cause.

---

### Post by rsambuca on 2007-04-12
Works fine here.  firefox 2.0.0.3 with no special scripts.

---

