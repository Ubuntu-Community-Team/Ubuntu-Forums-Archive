---
title: "messed up cursor and symlink"
date: 2014-07-19
forum: General Help
---

### Post by Karan_Sharma on 2014-07-19
Hi All,

I was trying to manually install a cursor and have it in use globally. I looked up threads and just screwed up. Right now the problem I have is as follows:

```


sudo update-alternatives --auto x-cursor-theme
update-alternatives: error: cannot stat file '/etc/alternatives/x-cursor-theme': Too many levels of symbolic links


```

If I do 

```

sudo update-alternatives --config x-cursor-theme


```

and then run the above, I get this error. For now I would like the Adwaita and fix the mess I made.

```


sudo update-alternatives --config x-cursor-theme
There are 12 choices for the alternative x-cursor-theme (providing /etc/alternatives/x-cursor-theme).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme   100       auto mode
  1            /etc/X11/cursors/core.theme               30        manual mode
  2            /etc/X11/cursors/handhelds.theme          20        manual mode
  3            /etc/X11/cursors/oxy-black.theme          40        manual mode
  4            /etc/X11/cursors/oxy-blue.theme           40        manual mode
  5            /etc/X11/cursors/oxy-white.theme          50        manual mode
  6            /etc/X11/cursors/oxy-yellow.theme         40        manual mode
  7            /etc/X11/cursors/oxy-zion.theme           40        manual mode
  8            /etc/X11/cursors/redglass.theme           20        manual mode
  9            /etc/X11/cursors/whiteglass.theme         20        manual mode
  10           /usr/share/icons/Adwaita/cursor.theme     90        manual mode
  11           /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode
  12           /usr/share/icons/DMZ-White/cursor.theme   100       manual mode

Press enter to keep the current choice
[*], or type selection number: 10
update-alternatives: using /usr/share/icons/Adwaita/cursor.theme to provide /etc/alternatives/x-cursor-theme (x-cursor-theme) in manual mode
update-alternatives: error: unable to install `/etc/alternatives/x-cursor-theme.dpkg-tmp' as `/etc/alternatives/x-cursor-theme': No such file or directory


```

---

### Post by grumblebum2 on 2014-07-20
For me the default theme here in ubuntu 14.04 is DMZ-White.
Try these commands to set back to default.

```
CURSOR=DMZ-White
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```

Logout and back in.

What symlink command did you use?
You shouldn't need to symlink.
Provide a link to the theme you tried to install and I'll show how I would install.

---

### Post by Karan_Sharma on 2014-07-20
Hi grumblebum2

That did not seem to work. Here is what I get-
```

karansh@karansh-Aspire-V5-573G:~$ CURSOR=Adwaita
karansh@karansh-Aspire-V5-573G:~$ gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
karansh@karansh-Aspire-V5-573G:~$ sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
[sudo] password for karansh: 
update-alternatives: error: cannot stat file '/etc/alternatives/x-cursor-theme': Too many levels of symbolic links
karansh@karansh-Aspire-V5-573G:~$ 

```

As far as what commands I used; I did the following to add the theme-
```

sudo update-alternatives --install /etc/alternatives/x-cursor-theme x-cursor-theme /usr/share/icons/<Cursor> 51

```

Which I found on [http://ubuntuforums.org/showthread.php?t=1974227](http://ubuntuforums.org/showthread.php?t=1974227)
Kind of stupid of me to not read the whole thread. Ever since I did this I would get the above issue. So I did-
```

unlink /etc/alternatives/x-cursor-theme
```
Then I was able to run update-alternates. However same error would come once I attempted to select the mouse cursor. Since then I've been trying to fix.
I feel stupid for doing this :(

---

### Post by grumblebum2 on 2014-07-20
So you don't currently have an **/etc/alternatives/x-cursor-theme** file ?

---

### Post by Dennis N on 2014-07-20
Post the output of:

```
update-alternatives --display x-cursor-theme
```

It can help show what's wrong.

---

### Post by Karan_Sharma on 2014-07-20
Here's the output.

```

karansh@karansh-Aspire-V5-573G:~$ update-alternatives --display x-cursor-theme
x-cursor-theme - manual mode
  link currently points to /etc/alternatives/x-cursor-theme
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/oxy-black.theme - priority 40
/etc/X11/cursors/oxy-blue.theme - priority 40
/etc/X11/cursors/oxy-white.theme - priority 50
/etc/X11/cursors/oxy-yellow.theme - priority 40
/etc/X11/cursors/oxy-zion.theme - priority 40
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/Adwaita/cursor.theme - priority 90
/usr/share/icons/DMZ-Black/cursor.theme - priority 30
/usr/share/icons/DMZ-White/cursor.theme - priority 100
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.

```

---

### Post by Dennis N on 2014-07-20
The link is pointing to itself, which is a no-no. Which cursor do you want?

---

### Post by Karan_Sharma on 2014-07-20
The attachment is a screenshot of what I get when I attempt to open x-cursor-theme with gedit.

---

### Post by Karan_Sharma on 2014-07-20
Hi dennis,

Lets go with anything (DMZ white say). I just dont want this error to pop up.

---

### Post by Dennis N on 2014-07-20
Use this command to use Adwaita:

```
sudo ln -sf /usr/share/icons/Adwaita/cursor.theme /etc/alternatives/x-cursor-theme
```

Use this command to to use DMZ-White:

```
sudo ln -sf /usr/share/icons/DMZ-White/cursor.theme /etc/alternatives/x-cursor-theme
```

---

### Post by Karan_Sharma on 2014-07-20
Dennis,

Same thing with symbolic links. Here's the output-

```
karansh@karansh-Aspire-V5-573G:~$ sudo ln -sf /usr/share/icons/DMZ-White/cursor.theme /etc/alternatives/x-cursor-theme
[sudo] password for karansh: 
ln: failed to access &#8216;/etc/alternatives/x-cursor-theme&#8217;: Too many levels of symbolic links
karansh@karansh-Aspire-V5-573G:~$ 


```

---

### Post by Dennis N on 2014-07-20
Let's see if anything at all changed. Post the results of the command in post #5 again.

---

### Post by Karan_Sharma on 2014-07-20
Dennis,

I choose DMZ white. Here's the output again-
```

karansh@karansh-Aspire-V5-573G:~$ update-alternatives --display x-cursor-theme
x-cursor-theme - manual mode
  link currently points to /etc/alternatives/x-cursor-theme
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/oxy-black.theme - priority 40
/etc/X11/cursors/oxy-blue.theme - priority 40
/etc/X11/cursors/oxy-white.theme - priority 50
/etc/X11/cursors/oxy-yellow.theme - priority 40
/etc/X11/cursors/oxy-zion.theme - priority 40
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/Adwaita/cursor.theme - priority 90
/usr/share/icons/DMZ-Black/cursor.theme - priority 30
/usr/share/icons/DMZ-White/cursor.theme - priority 100
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.


```

---

### Post by Dennis N on 2014-07-20
Well, it's exactly the same. The link still points to itself, so nothing happened at all. I am puzzled by the "failed to access" error. Perhaps a legitimate target is needed, and in your case there isn't one for the current link.

If no other solution is offered on the forum, I would think of trying two things:

1) Delete the symbolic link x-cursor-theme and then re-create it correctly.
2) It might be necessary to remove the alternative "x-cursor-theme" and then install it again. There are commands to do that, but I have never used them and I am a bit hesitant to try for the first time on someone else's system. 

If it was my computer, I would try #1 first (the commands are easy to make), but again I don't want to experiment with your computer as if I knew exactly what the result would be.  

For now, I suggest you wait a bit and see what else might be suggested. I will check this thread tomorrow and see what develops.

---

### Post by grumblebum2 on 2014-07-20
I tested and when /etc/alternatives/x-cursor-theme links back to itself, the command to create a link fails.
I would do as in Dennis's #1...
eg
```
sudo rm -i /etc/alternatives/x-cursor-theme
```
answer **yes**

then try to create the link again....
```
sudo ln -sf /usr/share/icons/DMZ-White/cursor.theme /etc/alternatives/x-cursor-theme
```


Try the commands in [**_[COLOR="#B22222"]post#2[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2235265&p=13077859#post13077859") again which should reset everything to DMZ-White.

---

### Post by Dennis N on 2014-07-20
Hello Karan_Sharma,

I hope the suggestions and commands in post #14 and post #15 will repair the x-cursor-theme symlink. But if not, here is a procedure to change the cursor which doesn't rely update-alternatives at all, so it should work when x-cursor-theme is broken as in your case - at least until it is repaired. I have tested it and it works fine on the test system. Details below.  

Here are the steps - I changed the current cursor to a new one, AeroM. The cursor folder must be in **/usr/share/icons**. Of course, use the name for your cursor instead of AeroM.

**Part 1**: Use the terminal     
```
dmn@Zotac:~$ cd /usr/share/icons
dmn@Zotac:/usr/share/icons$ sudo mv default default-old
dmn@Zotac:/usr/share/icons$ sudo ln -s AeroM default

```
  
**Part 2**: Use your systems settings tool to select the new cursor (in my test, AeroM). Log out and back in is necessary.

**For Lubuntu**  (where I tested this), Menu > Preferences > Customized Look and Feel >  Mouse Cursor > select AeroM and Click the Apply button. Then log out and back in.

**For Ubuntu**, you would use whatever settings tool does the cursor selection (I am unable to test in Ubuntu - not available). Then log out and back in.

To change the cursor in the future, I used these commands to change to the cursor Pulse-Glass:

```
dmn@Zotac:~$ cd /usr/share/icons
dmn@Zotac:~$ sudo rm default
dmn@Zotac:/usr/share/icons$ sudo ln -s Pulse-Glass default
```

Repeat Part 2.

(Comment: For convenience in changing cursor, change back to alternatives when you get this solved.  Just delete the link default, and then rename default-old to default. After the test, I did change mine back to use alternatives and x-cursor-theme.)

---

