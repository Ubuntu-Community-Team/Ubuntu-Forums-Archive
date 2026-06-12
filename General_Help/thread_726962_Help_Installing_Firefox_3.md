---
title: "Help Installing Firefox 3"
date: 2008-03-17
forum: General Help
---

### Post by CD27 on 2008-03-17
I just downloaded firefox beta 3 on my desktop. I can't figure out how to install it though. I can't find it in symantic or add/remove programs and don't know how to just install it. I'm still stuck on the windows double-click and install theme, please help :(

---

### Post by jespdj on 2008-03-17
What exactly did you download and from where? Is it a .deb package (if yes, you should just be able to double-click it to install it), or a .tar.gz or some other kind of file?

---

### Post by CD27 on 2008-03-17
this is it:

file:///home/eric/Desktop/firefox-3.0b4.tar.bz2

i got it directly off the mozilla firefox website

...still can't get it to install though

---

### Post by scramasax on 2008-03-17
> **CD27 said:**
> this is it:

file:///home/eric/Desktop/firefox-3.0b4.tar.bz2

i got it directly off the mozilla firefox website

It's not as straightforward as you thought.  Here's a walk-through for the Beta2:

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

I couldn't tell you if anything had changed since -- for example, if that library he installs in the first step is still what you want.

But, quite honestly, beta software isn't intended for the general public, anyway.  In most cases it's best to wait till whatever it is you want is available from Canonical's repositories.

Is there some feature in the software that you really need that isn't in Firefox 2?

---

### Post by forrestcupp on 2008-03-17
Here are the directions from Mozilla's web site.  You just untar it to your /home directory and run the binary file straight from there.  To uninstall it, just delete that directory.  When it is released in the backports repos, you're better off removing this and installing it through the repos.


   1.  Download Firefox from the Firefox download page to your home directory.
   2. Extract the contents of the downloaded file.

      bash$ cd ~
      bash$ tar zxf firefox-*.tar.gz

   3. To start Firefox, run the firefox script in the firefox folder.

      bash$ ~/firefox/firefox


With this, you'll probably have to copy all of your plugins to this directory.

---

### Post by CD27 on 2008-03-17
thanks! Here's what I had to do. I did just as you said, put the package file there, extracted it there, then found the file named: firefox and drug it into the terminal, put the "sudo" command before it, ran it, and there we are.

Thanks alot guys!

---

### Post by Nepherte on 2008-03-17
I wouldn't recommend running firefox with sudo privileges all the time, actually don't run your web browser as root at all.

---

### Post by CD27 on 2008-03-17
Sorry, I screwed that one up. Take the file named firefox, drag it to the "start bar" (sorry, windows terminology again :() and launch it directly from there.

> **CD27 said:**
> thanks! Here's what I had to do. I did just as you said, put the package file there, extracted it there, then found the file named: firefox and drug it into the terminal, put the "sudo" command before it, ran it, and there we are.

Thanks alot guys!

---

### Post by forrestcupp on 2008-03-17
> **CD27 said:**
> Sorry, I screwed that one up. Take the file named firefox, drag it to the "start bar" (sorry, windows terminology again :() and launch it directly from there.

That should be perfect.  Just remember that you shouldn't need to run or open anything that's in your /home directory as sudo.

And the 'start bar' is called a 'panel' in Gnome.

---

### Post by KongKNoob on 2008-03-21
You can also install the beta, and still keep firefox 2, with just one command. Check out [this]("http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/") post over at Tombuntu. Works like a charm, I'm posting this from FF3 beta 4.

---

### Post by CD27 on 2008-03-22
To say the least, I tried out the Beta, and didn't like it at all. It has a bug where you can't go back once you've reached a page, and if you do go back and put the "back and forward" buttons up there, they don't work.

there were several other problems (guess i'll just wait till it's outta beta :P)

---

