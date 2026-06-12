---
title: "Trying to pass variable from Bash to Python"
date: 2014-05-03
forum: General Help
---

### Post by bonelifer on 2014-05-03
I'm using a bash script(userjob) for transcoding commercial cut videos via Handbrake from MythTV.  I want to have the script at the end send something to my GrowlForWindows installation on my Windows PC.  I'm using the gntp module for python(pip install gntp). The Send script is registered with Growl and can send. Now I'm modifying it to also hopefully send the Title info with the description. I've got everything working(ie in my test script with a fixed title, it would work), but when I'm trying to do the same in the userjob script I can't get it to work. I don't know sed, awk and etc. I've tried copying "BASENAME2" and editing it, but my knowledge isn't good enough to figure it out. Either the userjob immediately fails, or it works, but sends a empty variable.

Bash script(mythtv userjob script):
[http://pastebin.com/MQCEt1sM](http://pastebin.com/MQCEt1sM)

Python(GNTP send script):
[http://pastebin.com/B5VpRsVi](http://pastebin.com/B5VpRsVi)

If I just export BASENAME2 it works, but I would like the unmodified(clean name).

---

### Post by Vaphell on 2014-05-03
can't you just use a parameters like
```
python script.py some parameter "some other parameter"
```
and then use them in python? parameters are stored in sys.argv (a list)

```
$ python <(echo "import sys; print( sys.argv[1:] )") a b ccc "some string"
['a', 'b', 'ccc', 'some string']
```
ignore the **<(...)** part, python thinks it's a legit script file. As you can see passing stuff to python scripts is trivial.
Exporting variables sounds like an overkill.

If BASENAME is the one you want - *python script.py "$BASENAME"*
in python: [I]basename=sys.argv[1]
[/I]

btw, if it's supposed to be a bash script, then change the hashbang to #!/bin/**bash**
sh =/= bash

also prefer $() instead of backticks `` and avoid all-caps names. By convention important settings are stored in all-caps variables and you risk overwriting them by accident (shell won't complain), which can introduce subtle and not so subtle bugs. At least 1 lowercase char and you are golden.

---

### Post by bonelifer on 2014-05-03
I didn't write the original code.  Just reused it. Since my bash scripting is very basic, and I can't even wrap my head totally around sed or awk enough to do those, I try not to break stuff that is already working for me. Thanks for the tips, got it working. Needless to say no matter how good your Google FU is, if all the examples you find are too complex, it's hard to figure out. :)

---

