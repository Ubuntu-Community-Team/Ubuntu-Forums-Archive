---
title: "Cairo-dock Icons flicker"
date: 2014-04-30
forum: General Help
---

### Post by Ron McIlvaine on 2014-04-30
Hello,

I updated to Ubuntu 14.04 and I love it. I tried to install Cairo-Dock 3.3.2 (?) but the icon flicker as the cursor passes over the dock. I have a 4 year old Acer Aspire 5534 notebook computer with ATI Radeon HD3200 Graphics. Ubuntu makes it run great. I know it's not new or fast but it's what I have. Any ideas other than buy a newer computer? This is the only graphics problem i have encountered.

---

### Post by ihaake on 2014-05-01
-

---

### Post by ihaake on 2014-05-01
same to me.
I just upgraded from ubuntu 13.10 to 14.04 and didn't do anything to my cairo-installation.
In 13.10 everything was perfect
In 14.04 I got this flicker

And I got a solution.
Had to start cairo with **explicitly** using openGL: "cairo-dock -o"

After starting cairo from the dash "Cairo-Dock (Fallback Mode)" I get this dialog "Benutze (Use) OpenGL im Cairo-Dock" (for I am German :-)
And have to choose "**Nein (No)**" to get OpenGL support !!!
Weird!
But then it starts cairo **WITH** OpenGL. And you can make a "starter" from it.
You can check it by starting via command line. With and without the "-o" option.

Hope it works for you too.
Cheers, Ingo

---

