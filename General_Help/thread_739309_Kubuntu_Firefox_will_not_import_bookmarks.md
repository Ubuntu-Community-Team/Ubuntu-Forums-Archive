---
title: "Kubuntu Firefox will not import bookmarks"
date: 2008-03-29
forum: General Help
---

### Post by CoffeeBreath on 2008-03-29
Bookmarks>organize>file>import> yada yada.


Simply will not work. I looked at the .html that supposed to be generated and it list no bookmarks. Can't even copy them from the CL. In fact, even if I email the HTML file to myself from the Vista side, it still won't work. Imagine thinking, "hmm it worked in Vista but not linux." Anger is mounting. Any suggestions?

---

### Post by y-lee on 2008-03-29
Hmm how did you generate or obtain the file you are trying to import?

Your problem may have something to do with the difference between the way DOS/Windows and Unix/linux deals with text files, I had that problem once tho with a different program than FF.  If so you could try to use [tofrodos]("http://www.thefreecountry.com/tofrodos/index.shtml") to convert the windows text file into a Unix/linux text file. And then try to import the converted file. tofrodos is in the repos and after you install it **man tofrodos** to see how to use it. (man is a terminal command and enter that in a terminal and q exits the man program ...just in case you don't know)

Or you could do what i do to keep my FF bookmarks on my computers and in various OS's synced, install and use [Foxmarks add on]("https://addons.mozilla.org/en-US/firefox/addon/2410"). You have to create and account on foxmarks web site but the extension works great for me :)

---

### Post by CoffeeBreath on 2008-03-29
Thanks for responding Y- lee,
  From what I've seen Firefox (vista or kubuntu) stores it's bookmarks in a .html (not a text file) file in the default folder. But when I try to direct Firefox to one of these .html files to import it just does not give a !@#$. I've known this for a while but, today I am trying to import bookmarks from FF3 beta back to 2.0.0.12. 

In any case, this should just be running smoothly

---

### Post by y-lee on 2008-03-29
> From what I've seen Firefox (vista or kubuntu) stores it's bookmarks in a .html (not a text file) file in the default folder

Yeah firefox does store it's bookmarks in a html file BUT this is still a text file, html just means the text file is to be interpreted as hypertext, ie like a web page. for some reason the extra CR character (Carriage return) windows or dos puts in messes with some linux programs, I've known about that for a very long time from my experiences programming in C. Anyway it was just a thought since i can't reproduce your exact problem on my machine :confused:

> but, today I am trying to import bookmarks from FF3 beta back to 2.0.0.12. 

Good luck and btw didn't firefox [recently update to 2.0.013]("http://www.mozilla.com/en-US/firefox/")? I use swiftweasel myself (basically firefox compiled for speed) and manually install it. Planning on updating to 3.0 once it is outta beta.

---

### Post by CoffeeBreath on 2008-03-29
Thanks Y-lee

Firefox did upgrade recently. Just haven't done it myself yet.

i ended up exporting my FF3 bookmarks to .mozilla>blah blah blah. But, that was too difficult. At least I knew that hidden files exist. This really put a bitter taste in my mouth.

---

