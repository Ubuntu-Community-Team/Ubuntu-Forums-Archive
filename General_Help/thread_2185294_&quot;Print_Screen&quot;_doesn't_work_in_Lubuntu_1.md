---
title: "&quot;Print Screen&quot; doesn't work in Lubuntu 13.10?"
date: 2013-11-01
forum: General Help
---

### Post by vasa1 on 2013-11-01
Why does pressing "Print" do nothing in Lubuntu 13.10 for some users?

If pressing the "Print" or "Prnt Scrn" key does nothing, please read on. 

"Scrot" is the default screen capture utility in Lubuntu and `man scrot` has this:

>        scrot  is  a  screen capture utility using the imlib2 library to aquire
       and save images.  scrot has a  few  options,  detailed  below.  Specify
       [file]  as  the  filename  to save the screenshot to.  If [file] is not
       specified, a date-stamped file will be dropped in  the  current  direc&#8208;
       tory.


However, for some users of Lubuntu 13.10, no file is created anywhere in /home or its subfolders. 

One way to fix this is to edit **~/.config/openbox/lubuntu-rc.xml** (after making a backup for safety).

Open lubuntu-rc.xml with a text editor of your choice. Leafpad will do. Search for **print** or **Print**. You should get exactly four hits in an unmodified lubuntu-rc.xml:


```
    <!-- Take a screenshot of the current window with scrot when Alt+**Print** are pressed -->
    <keybind key="A-**Print**">
      <action name="Execute">
        <command>lxsession-default screenshot window</command>
      </action>
    </keybind>

```
and

```
    <!-- Launch scrot when **Print** is pressed -->
    <keybind key="**Print**">
      <action name="Execute">
        <command>lxsession-default screenshot</command>
      </action>
    </keybind>

```
Notice the contents between **<command>** and **</command>**.

In the first case, change `lxsession-default screenshot window` to `scrot -u -b`.
In the second case, change `lxsession-default screenshot` to `scrot`.

Save the file (as a plain text file) and exit the text editor.

Open a terminal, run `openbox --reconfigure`. You shouldn't get a pop-up informing you of errors. The prompt should return. That's all. *If you do get errors, it means there's something wrong with lubuntu-rc.xml* but that's not relevant here.

From now on, both **Print Screen** to print the whole screen and **Alt + Print Screen** to print just the active window should work as described in **man scrot**.

Check out **man scrot** and also [http://askubuntu.com/q/252281/25656](http://askubuntu.com/q/252281/25656).

---

### Post by amjjawad on 2013-11-02
Because this is a bug: [https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1233860](https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1233860)

And, the easiest and the simplest workaround is: ```
sudo apt-get install gnome-screenshot

```

At least, GNOME Screenshot has some nice features (GUI) and will help 'new' users :)

Thanks for posting that workaround, my friend :)

---

### Post by syntaxerror74 on 2014-01-30
Well, I think ksnapshot is even better than gnome-screenshot (but that may be a matter of taste) :)

---

### Post by sudodus on 2014-01-30
Thank you all for these helpful posts :-)

---

### Post by john-duck-sinnott on 2014-01-30
This fix doesn't do anything for me on my Lubuntu 13.10 :(  'Prt Sc' button still doesn't work, but it did work fine when I had Ubuntu 12.04 installed. I'll try some of the other suggestions

---

### Post by syntaxerror74 on 2014-01-31
John, could it be you're expecting something to **happen** on screen (pop up, flash, beep, move)? :D 

This is not the case. The fix works for me (Lubuntu 13.10 as well), but things remain **silent** as a mouse.

Taking a screenshot will work but you have to check your home directory where scrot has placed the file without noticing you about it in any way.
(Well, that's *no* ksnapshot (see above) which will **pop up** by itself when 'demonized' and you hit PrtSc :D)

---

### Post by tm007 on 2014-03-02
> **vasa1 said:**
> Why does pressing "Print" do nothing in Lubuntu 13.10 for some users?

If pressing the "Print" or "Prnt Scrn" key does nothing, please read on. 

"Scrot" is the default screen capture utility in Lubuntu and `man scrot` has this:



However, for some users of Lubuntu 13.10, no file is created anywhere in /home or its subfolders. 

One way to fix this is to edit **~/.config/openbox/lubuntu-rc.xml** (after making a backup for safety).

Open lubuntu-rc.xml with a text editor of your choice. Leafpad will do. Search for **print** or **Print**. You should get exactly four hits in an unmodified lubuntu-rc.xml:


```
    <!-- Take a screenshot of the current window with scrot when Alt+**Print** are pressed -->
    <keybind key="A-**Print**">
      <action name="Execute">
        <command>lxsession-default screenshot window</command>
      </action>
    </keybind>

```
and

```
    <!-- Launch scrot when **Print** is pressed -->
    <keybind key="**Print**">
      <action name="Execute">
        <command>lxsession-default screenshot</command>
      </action>
    </keybind>

```
Notice the contents between **<command>** and **</command>**.

In the first case, change `lxsession-default screenshot window` to `scrot -u -b`.
In the second case, change `lxsession-default screenshot` to `scrot`.

Save the file (as a plain text file) and exit the text editor.

Open a terminal, run `openbox --reconfigure`. You shouldn't get a pop-up informing you of errors. The prompt should return. That's all. *If you do get errors, it means there's something wrong with lubuntu-rc.xml* but that's not relevant here.

From now on, both **Print Screen** to print the whole screen and **Alt + Print Screen** to print just the active window should work as described in **man scrot**.

Check out **man scrot** and also [http://askubuntu.com/q/252281/25656](http://askubuntu.com/q/252281/25656).

Thanks for the instructions. This is far easier than installing ksnapshot. ksnapshot didn't work for me anyways and it left a re-occurring .kde folder, after uninstalling it, that keeps appearing every time I delete it.

BTW is there a way I can change the save location and file type? When I press Alt+Print, or Print it places the screen shot in /home/user directory, it would be nice to put it in the /home/user/Picture directory.

---

### Post by vasa1 on 2014-03-02
> **tm007 said:**
> Thanks for the instructions. This is far easier than installing ksnapshot. ksnapshot didn't work for me anyways and it left a re-occurring .kde folder, after uninstalling it, that keeps appearing every time I delete it.
I stay away from installing software beginning with "k" unless I'm using Kubuntu which I'm not :) Some GNOME software also rams down a lot of stuff which may not be needed.

As a general precaution, I run *sudo apt-get install -s package_name* to get a simulation of what will be installed. I also prefer *install --no-install-recommends* over plain *install* when appropriate.

---

### Post by vasa1 on 2014-03-02
> **tm007 said:**
> ...
BTW is there a way I can change the save location and file type? When I press Alt+Print, or Print it places the screen shot in /home/user directory, it would be nice to put it in the /home/user/Picture directory.

This is what I'm using now in my *rc.xml*. If you're using a Lubuntu session, it would go into *~/.config/openbox/lubuntu-rc.xml*:

```

    <!-- ##### Take a delayed screenshot of the current window with scrot when W+Print are pressed -->
    <keybind key="W-Print">
      <action name="Execute">
        <command>scrot -u -b -d 5 -q 100 ~/Desktop/%b%d::%H%M%S.png</command>
      </action>
    </keybind>
    <!-- ##### Take an immediate full screenshot when Print is pressed -->
    <keybind key="Print">
      <action name="Execute">
        <command>scrot -b -q 100 ~/Desktop/%b%d::%H%M%S.png</command>
      </action>
    </keybind>

```
You can change *~/Desktop* to whatever else you like.
You can reduce **-q 100** to something else if you feel the image files are too big. **75** is the default.

Why do you want to change the file type? You can use **.jpeg** instead of **.png**.

**Helpful link**: [http://www.freesoftwaremagazine.com/articles/how_to_take_screenshots_with_scrot](http://www.freesoftwaremagazine.com/articles/how_to_take_screenshots_with_scrot)

---

### Post by Rex Bouwense on 2014-03-02
Hey guys take a breath.  Back in October (yes a month after Lubuntu 13.10 was released) I noticed that "Prt Sc" didn't work.  OK.  Then in November amjjawad (in this same thread) said install Screenshot and then you would be able to print the screen.  I did that and it is a wonderful work-around.  I recommend it to one and all.  While we all want bugs fixed, in reality they are never going to get fixed as fast as we want.  I for one will wait satisfied that there is a viable work-around until the developers get around to the patch.

---

### Post by el_gallo_azul on 2014-09-27
I came here as a result of wanting to find out how to take a screenshot in Lubuntu 14.04, because it didn't seem to be working.

I happened to read the post by @syntaxerror74, and went to /home/user to have a look, and sure enough there were a bunch of screenshots from all of my attempts. It was just that there was no indication that a screenshot had been taken.

I imagine that it is possible that it is indeed working for most people who have posted here, and that they hadn't seen the resulting screenshots at the time that they posted.

BTW, Shift+PrtScn doesn't seem to work, but Alt+PrtScn works fine.

---

### Post by vasa1 on 2014-09-27
> **el_gallo_azul said:**
> ...
BTW, Shift+PrtScn doesn't seem to work, but Alt+PrtScn works fine.
Only the key combinations defined by default or those subsequently defined by you in ~/.config/openbox/lubuntu-rc.xml will work. Did you assign shift+PrntScrn to anything related to scrot?

I'm currently using just the two key combinations shown below:```
    <!-- ##### Take an immediate full screenshot when Print is pressed -->
    <keybind key="Print">
      <action name="Execute">
        <command>scrot -b ~/Desktop/%b%d::%H%M%S.png</command>
      </action>
    </keybind>
    <!-- ##### Take a delayed screenshot of the active window with scrot when W+Print are pressed -->
    <keybind key="W-Print">
      <action name="Execute">
        <command>scrot -u -b -d 5 ~/Desktop/%b%d::%H%M%S.png</command>
      </action>
    </keybind>

```

Just tried this:```
    <keybind key="A-Print">
      <action name="Execute">
        <command>scrot -b ~/Desktop/scrot.png</command>
      </action>
    </keybind>

```Works.

---

### Post by syntaxerror74 on 2014-10-23
> **el_gallo_azul said:**
> I came here as a result of wanting to find out how to take a screenshot in Lubuntu 14.04, because it didn't seem to be working.

I happened to read the post by @syntaxerror74, and went to /home/user to have a look, and sure enough there were a bunch of screenshots from all of my attempts. It was just that there was no indication that a screenshot had been taken.

I'm very glad to hear it helped you. :) scrot does its job very silently (but just greatly for my purpose).

Maybe future 'Buntus could add an option for scrot to send some message via dbus to the notification daemon?? Though I can do without it, a myriad of people surely won't want to.

---

