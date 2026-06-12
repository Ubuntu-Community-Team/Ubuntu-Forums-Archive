---
title: "Font Gone Haywire"
date: 2007-10-22
forum: General Help
---

### Post by kingdogbert on 2007-10-22
So I'm finally got this tool called 3DMagic to build after working all day on it. When I finally try to run it, the terminal font goes crazy, and tool's gui doesn't load. Can anyone give me a hint as to where to start looking for the source of the font problem? Thanks

Crazy terminal font:
[http://img86.imageshack.us/img86/7159/screenshotoo6.png]("http://img86.imageshack.us/img86/7159/screenshotoo6.png")
You can see the craziness at the bottom of the right terminal.

---

### Post by dchenbecker on 2007-10-22
From the screenshot you posted it looks like the app is spitting out some non-character characters. When that happens it can hose the terminal so that later characters don't display. What's happening is that the terminal is supposed to interpret some characters to control display behavior (font, color, codepage for international text, etc) and the output from the program is mistakenly nuking the terminal. You can type "reset" and hit enter (you'll see gibberish while you're typing) and that should restore the terminal. I'd say you're bigger problem is figuring out why 3DMagic is outputting non-ascii characters anyways. Is it a foreign program?

---

### Post by kingdogbert on 2007-10-22
Thanks for letting me know about reset. Much less of a pain than restarting the terminal :)

Anyways, there's nothing wrong with 3DMagic. It's a VLSI tool developed at MIT. It runs just fine on my school puter, which is running some version of RedHat. I'm trying to get it running my laptop in Gutsy for mobile work. I'm trying to get some hints as to where the link might have gone bad, most likely between 3DMagic and X11.

---

