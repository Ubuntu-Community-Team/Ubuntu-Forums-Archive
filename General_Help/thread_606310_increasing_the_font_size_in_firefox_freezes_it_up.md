---
title: "increasing the font size in firefox freezes it up"
date: 2007-11-07
forum: General Help
---

### Post by ridetheteapot on 2007-11-07
if i try to change the font size in firefox (via ctrl++ or mouse wheel)
i opened the jsconsole and got a bunch of warnings pertaining to css (this is before i attempt to change the font size)

Warning: Unknown property '_margin-left'.  Declaration dropped.
Source File: [http://www.wnyc.org/inc/css/screen.css](http://www.wnyc.org/inc/css/screen.css)
Line: 33
Warning: Expected end of value for property but found 'font-weight'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-dcc708dc-00074.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-dcc708dc-00074.css)
Line: 1961

this kind of stuff seems to only be css pages

and also got a few errors like
Error: $ is not defined
Source File: [http://ubuntuforums.org/forumdisplay.php?f=131](http://ubuntuforums.org/forumdisplay.php?f=131)
Line: 2514

what is going on?

I have to say i really don't like firefox anymore. Went from love to hate over the last few months. Even if the font size would increase it really mangles the pages... the worst is that on sourceforge the search bar always gets covered by an add if the font it too big, but its better then squinting.

the ironic thing is that i just switched over from opera, which is very nice, espesially with font size increases (the zoom funtion), but i just couldn't get the java plugin to work

---

### Post by mpierce on 2007-11-07
Save all your bookmarks so you can restore. Check and find out which extensions you are using that you want to reinstall. 

Blow it away and reinstall. I once had a corrupted version and gave up; reinstalling did the trick. 

Blow it away with sudo dpkg -P firefox or mozilla-firefox you can find out what you are using with:
   dpkg -l | grep mozilla or dpkg -l | grep firefox

It's quick, easy and painless!

Hope this helps...

---

### Post by ridetheteapot on 2007-11-07
heh, no that didn't do anything ( i did try for tryings sake though)
its was a fresh install, no extensions or anything.
basicly i installed came to ubuntuforums tryed to make the text bigger and crashed.
i can go to a site like google or wikipedia nad increase the font size and then come to sites like ubuntuforums and i will have nice big text, but that is not a nice workaround.
i will probably go back to opera and dump firefox and thunderbird again.

opera is just so much nicer even if it is qt. just need to get the java plugin working
actually i only installed firefox cause i forgot to deselect it after the java plugin selected it as a dependancy. but it is not, you can use the plugin or other browsers, the mplayer plugin does the same thing, which is bothersome

---

