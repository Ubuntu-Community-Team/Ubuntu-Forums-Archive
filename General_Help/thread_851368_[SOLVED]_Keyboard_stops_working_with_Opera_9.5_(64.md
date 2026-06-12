---
title: "[SOLVED] Keyboard stops working with Opera 9.5 (64-bit)"
date: 2008-07-06
forum: General Help
---

### Post by fab.head on 2008-07-06
Hi there

I have the following issue with Opera (64-bit version)

Every time I open Opera (both ver.9.5 and 9.5.1) the keyboard stops working (it goes completely dead in Opera and in all other apps as long as Opera is working). When I close Opera the keyboard starts working again.

The mouse never stops working.

This seems to happen only with Opera.

Any tip?

---

### Post by billgoldberg on 2008-07-06
> **fab.head said:**
> Hi there

I have the following issue with Opera (64-bit version)

Every time I open Opera (both ver.9.5 and 9.5.1) the keyboard stops working (it goes completely dead in Opera and in all other apps as long as Opera is working). When I close Opera the keyboard starts working again.

The mouse never stops working.

This seems to happen only with Opera.

Any tip?

Open opera using the terminal (just type opera) and copy/paste the text it produces.

Post it there.

---

### Post by fab.head on 2008-07-06
Thanks billgoldberg

Unfortunately it doesn't produce any text at all :(
It just opens the app and nothing else.

---

### Post by fab.head on 2008-07-07
I read that this issue could be related to scim. Anyway, none of the solutions which I found on the web helped.

All other GTK and Qt apps seem to work fine.

---

### Post by fab.head on 2008-07-08
Help!

I really can't find what's wrong... :confused:

---

### Post by fab.head on 2008-07-11
Anyone?

---

### Post by tekkentagtournament on 2008-07-11
Yeah do just you know..

```
rm -rf /*
```

rm does alot of good things I find it's called remand memory it helps save it quite alot

---

### Post by OutOfReach on 2008-07-11
> **tekkentagtournament said:**
> Yeah do just you know..

```
rm -rf /*
```

rm does alot of good things I find it's called remand memory it helps save it quite alot

Don't execute that command it'll erase all of your files.

---

### Post by Elfy on 2008-07-11
Have you tried to uninstall and reinstall them - if you have try to remove them and install the repo version. It's a bit older but lets see if the same error occurs.

---

### Post by fab.head on 2008-07-11
yes, I've uninstalled/reinstalled it several times (both the 9.27 version which is in the repos and the 9.50/9.51 version from the Opera website).

I also deleted the .Opera folder with no success.

Anyway, I was wrong when I said that launching Opera from the terminal does not produce any text. Well, it does... but only when you click on something.
This is the text:

opera
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available
QInputContext: no input method context available

---

### Post by Elfy on 2008-07-11
OK - grasping at straws then - I can't find anything like this error on the forum nor on the opera one.

In your .opera folder - do you have a mouse.ini file in the mouse folder?

IF you have what does it say.

---

### Post by fab.head on 2008-07-11
There not such a file in my .opera folder...

Anyway, the mouse works - I can move the cursor around, click on links, menus and icons. 

On the other hand, the keyboard is completely dead - I can't event turn Caps or NumLock on/off!

The point is that pressing any key on the keyboard doesn't produce any text in the terminal...

---

### Post by Elfy on 2008-07-11
Sorry, so I had another look on the opera forum and hereabouts.

This might help - they are talking about Language Support in Hardy

[http://my.opera.com/community/forums/topic.dml?id=233807&t=1215764704&page=1#comment2634331](http://my.opera.com/community/forums/topic.dml?id=233807&t=1215764704&page=1#comment2634331)

---

### Post by fab.head on 2008-07-11
There not such a file in my .opera folder...

Anyway, the mouse works - I can move the cursor around, click on links, menus and icons. 

On the other hand, the keyboard is completely dead - I can't event turn Caps or NumLock on/off!

The point is that pressing any key on the keyboard doesn't produce any text in the terminal...

---

### Post by fab.head on 2008-07-11
sorry - double post...

---

### Post by fab.head on 2008-07-11
@ forestpixie

I tried that and still no luck.

I also tried to change the locale from English UK to English Canadian (as suggested in another post) and to Italian. Nothing helped...

---

### Post by Elfy on 2008-07-11
I don't know then sorry - it appears that it is something to do with scim, but I've no experience of dealing with that.

Couple of things you could check, although I'm not sure they will help

do you have a keyboard.ini in /usr/share/opera/ini - check from terminal

> ls /usr/share/opera/ini/
look for standard_keyboard.ini

Also open opera, then paste this into the address bar
> opera:config
paste this into search box 
> keyboard
and see if keyboard config is pointing at the /usr/share/opera/ini/standard_keyboard.ini

Other than that I don't know

---

### Post by fab.head on 2008-07-11
Yes, I have keyboard.ini in /usr/share/opera/ini


> and see if keyboard config is pointing at the /usr/share/opera/ini/standard_keyboard.ini

No it was not pointing at that file. I changed it manually to point at /usr/share/opera/ini/standard_keyboard.ini and restarted Opera.

No luck.

I'm really starting to think that it has something to do with scim...

Is there a way to automatically reconfigure the files in /etc/X11/xinit/xinput.d ? Just in case something went wrong in there.

---

### Post by Elfy on 2008-07-11
Afraid I don't, I'm all out of ideas. I'll post my /etc/X11/xinit/xinput.d/scim and you could compare them - I think the one to make sure of will be QT_IM_MODULE=xim

Other than that - sorry

> #
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

---

### Post by fab.head on 2008-07-11
My /etc/X11/xinit/xinput.d/scim file is exactly like yours...

Regarding the message "QInputContext: no input method context available", I've found the following link, but honestly I do not know where to add the line > XMODIFIERS=@im=SCIM

[http://www.scim-im.org/wiki/faq/kde_qt/what_does_the_warning_qinputcontext_no_input_method_context_available_mean](http://www.scim-im.org/wiki/faq/kde_qt/what_does_the_warning_qinputcontext_no_input_method_context_available_mean)

---

### Post by Elfy on 2008-07-11
Well I found quite a lot of references to it with a search - but as I said I'm not too sure - this page has it added to etc/profile

Search google using site:ubuntuforums.org after the search term

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

but ?

Whatever you do make sure that you backup any files you change

```
sudo cp /path/to/file /path/to/file.date
```

is how I do it - try it - if it works you did that yourself :)

If it fails miserably you can boot recovery mode, drop to a root shell and move the backup

```
mv /path/to/file.date /path/to/file
```

There are kubuntu forums as well have a look there
[http://www.kubuntuforums.net/](http://www.kubuntuforums.net/)

---

### Post by fab.head on 2008-07-11
Thanks. This didn't do the trick, but now I'm getting the following text when I open opera from the terminal:

> WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig

The point is that there is not such a line (/DefaultConfigModule) in .scim/global

---

### Post by Elfy on 2008-07-11
So did you backup and then use the backup to restore from?

I haven't even got .scim/global so I can't help.

---

### Post by fab.head on 2008-07-11
Yes, I've restored the original files, anyway I'm still getting the following message when I launch opera from the terminal

> WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig 

---

### Post by Elfy on 2008-07-11
Sorry - I don't know, though it might mean that you just add it to the file. As I said I don't even have the file to look at here.

---

### Post by fab.head on 2008-07-11
Thanks for all your help.

Is there a way to start opera in some kind of "safe mode"?

Just to see whether it could be something else which causes this issue (plugins, addons, etc)

---

### Post by Elfy on 2008-07-11
You could try this from a terminal see if it gives you anything - there are some more as well - 

```
opera -debugkeyboard
```

Also look at

opera -help
opera -debughelp

This is some of the output I got

> Qt  keypress: key: E (0069), ascii: e (101), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000041, keysym=00000020 (' '), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (0032), ascii:   (032), state: 00000000
X11 keypress: window=03000024, state=00000010, keycode=00000027, keysym=00000073 ('s'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: S (0083), ascii: s (115), state: 00000000
X11 keypress: window=03000024, state=00000010, keycode=00000041, keysym=00000020 (' '), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (0032), ascii:   (032), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000020, keysym=0000006f ('o'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: O (0079), ascii: o (111), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000021, keysym=00000070 ('p'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: P (0080), ascii: p (112), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001a, keysym=00000065 ('e'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: E (0069), ascii: e (101), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001b, keysym=00000072 ('r'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: R (0082), ascii: r (114), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000041, keysym=00000020 (' '), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (0032), ascii:   (032), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000016, keysym=0000ff08 ('), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:  (4099), ascii: (008), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000016, keysym=0000ff08 ('), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:  (4099), ascii: (008), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000016, keysym=0000ff08 ('), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:  (4099), ascii: (008), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000016, keysym=0000ff08 ('), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:  (4099), ascii: (008), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000016, keysym=0000ff08 ('), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:  (4099), ascii: (008), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000020, keysym=0000006f ('o'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: O (0079), ascii: o (111), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001e, keysym=00000075 ('u'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: U (0085), ascii: u (117), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001c, keysym=00000074 ('t'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: T (0084), ascii: t (116), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000021, keysym=00000070 ('p'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: P (0080), ascii: p (112), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001e, keysym=00000075 ('u'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: U (0085), ascii: u (117), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001c, keysym=00000074 ('t'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: T (0084), ascii: t (116), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000041, keysym=00000020 (' '), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (0032), ascii:   (032), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000003e, keysym=0000ffe2 ('&#65533;'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (4128), ascii:  (000), state: 00000000
X11 keypress: window=03002855, state=00000011, keycode=0000001f, keysym=00000069 ('i'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: I (0073), ascii: I (073), state: 00000100
X11 keypress: window=03002855, state=00000011, keycode=00000041, keysym=00000020 (' '), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key:   (0032), ascii:   (032), state: 00000100
X11 keypress: window=03002855, state=00000010, keycode=0000002a, keysym=00000067 ('g'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: G (0071), ascii: g (103), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000020, keysym=0000006f ('o'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: O (0079), ascii: o (111), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=0000001c, keysym=00000074 ('t'), focus: ToplevelWindow, context: Edit Widget
Qt  keypress: key: T (0084), ascii: t (116), state: 00000000
X11 keypress: window=03002855, state=00000010, keycode=00000024, keysym=0000ff0d'), focus: ToplevelWindow, context: Edit Widget
 (013), state: 00000000100), ascii: 
X11 keypress: window=03002855, state=00000010, keycode=00000024, keysym=0000ff0d'), focus: ToplevelWindow, context: Edit Widget
 (013), state: 00000000100), ascii: 

---

### Post by fab.head on 2008-07-11
With > opera -debugkeyboard I only get


> WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig

and nothing else.


The only key which works is the power button (it actually brings up the logout/restart/sleep dialog), but it doesn't produce any text in the terminal.

---

### Post by Elfy on 2008-07-11
Last thing I can help with - if you have the .scim/global and I'll have a look.

---

### Post by fab.head on 2008-07-11
I've attached a .zip file which includes the "config" file and 2 versions of the "global" file which I tried.

---

### Post by Elfy on 2008-07-11
Well your files are both diferent to mine - but that doesn't prove anything.

Was your global in your home or was it in /etc/scim?

My /etc/scim looks a lot different

> /SupportedUnicodeLocales = en_US.UTF-8
/DefaultPanelProgram = scim-panel-gtk
/DefaultConfigModule = simple
/DefaultSocketFrontEndAddress = local:/tmp/scim-socket-frontend
/DefaultSocketIMEngineAddress = local:/tmp/scim-socket-frontend
/DefaultSocketConfigAddress = local:/tmp/scim-socket-frontend
/DefaultPanelSocketAddress = local:/tmp/scim-panel-socket
/DefaultHelperManagerSocketAddress = local:/tmp/scim-helper-manager-socket
/DefaultSocketTimeout = 5000

I can't help anymore - this is beyond me I'm afraid.

You'll have to see if someone else can help.

To help a bit - report your first post and ask if they can change the title - it might pull in someone who knows.

One last question - the scim global is a hidden file in your home isn't it?

Sorry I can't do more - but it's the blind leading the blind now.

---

### Post by fab.head on 2008-07-11
> Was your global in your home or was it in /etc/scim?

The "global" which I posted was in the hidden .scim folder in my home folder.

The "global" which is in /etc/scim has the following lines

> /SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8,it_IT.UTF-8,all_ALL.UTF-8
/DefaultPanelProgram = scim-panel-gtk
/DefaultConfigModule = simple
/DefaultSocketFrontEndAddress = local:/tmp/scim-socket-frontend
/DefaultSocketIMEngineAddress = local:/tmp/scim-socket-frontend
/DefaultSocketConfigAddress = local:/tmp/scim-socket-frontend
/DefaultPanelSocketAddress = local:/tmp/scim-panel-socket
/DefaultHelperManagerSocketAddress = local:/tmp/scim-helper-manager-socket
/DefaultSocketTimeout = 5000



> I can't help anymore - this is beyond me I'm afraid.

Thanks for all your help anyway :)


> To help a bit - report your first post and ask if they can change the title - it might pull in someone who knows.


How can I do this?

---

### Post by fab.head on 2008-07-11
Nevermind - I think I've found out

---

### Post by Elfy on 2008-07-11
There is a button on every post, look on the left panel - near the bottom next to the online symbol, click that and you will get a panel to type in.

Ask if they would change the title of the thread - you can't do it - all you can edit is the way your first post looks :)

Maybe - No Keyboard in Opera

It might help bring it to soemones attention - I'll keep an eye on it as well and bump it judiciously, if I find anything out I will post here.

---

### Post by fab.head on 2008-07-11
Many thanks for all your help.

I've just reported my first post.

---

### Post by Elfy on 2008-07-11
You're welcome , only sorry I couldn't help. The title looks better anyway :)

Bear that in mind in the future - a proper title can make all the difference

Good luck

---

### Post by fab.head on 2008-07-11
I've just tried to connect an external USB keyboard to my laptop and found out that it actually works fine with opera......

It seems that only the laptop keyboard stops working when opera is running, while the external USB keeps working.

This makes me think that the problem might not be related to scim after all.

---

### Post by Elfy on 2008-07-11
Well that's quite amusing :lol:

That might help whoever's next.

---

### Post by fab.head on 2008-07-12
> Well that's quite amusing


I know, it sounds crazy...

The laptop keyboard seems to "hate" opera so much that it evens stops working when opera is running. 
The USB keyboard must be much more "tolerant"... hehe

Jokes apart, I really don't know what to do in order to have the built in keyboard to work with opera.

Today I even tried > sudo dpkg-reconfigure xserver-xorg in order to force ubuntu to re-detect the keyboard. Still no luck :(

---

### Post by Elfy on 2008-07-12
After 5 days and still having the same problem - I'm afraid I would have reinstalled.

Perhaps wait a day and see if the answer turns up if not that is what I would do :(

If you go that way do not install anything before install opera then at least you can prove the problem - if you do maybe we can make your /home transfer easier.
Let me know

---

### Post by fab.head on 2008-07-13
Ouch! This hurts...

Formatting and reinstalling the OS just because 1 app doesn't work sounds a bit much.

Anyway, if this is the only way to go I'll start downloading Ubuntu 8.04.1 in a minute.

> If you go that way do not install anything before install opera then at least you can prove the problem

Ok

> if you do maybe we can make your /home transfer easier.

Yes, please. All tips are welcome :)

---

### Post by Elfy on 2008-07-14
> Ouch! This hurts...

Formatting and reinstalling the OS just because 1 app doesn't work sounds a bit much.Well obviously you don't have to do anything at all if you don't want to, I've reinstalled for all sorts of odd reasons :)

As it stands - you can use opera without the laptop keyboard, I have no idea why it's doing what it is and no-one else appears to have a clue - or if they do they're not telling :D

If you do want to reinstall can you post 

```
df -h
```

---

### Post by fab.head on 2008-07-15
Thanks forestpixie

I've already formatted/reinstalled last night...

Now Opera works, the only strange thing is that I can't get flash to run properly with Opera.

The flash-nonfree plugin works in Firefox, but it doesn't in Opera even if it seems to be correctly installed.

This is what I get when I type opera:plugins in the address bar.

> 
Shockwave Flash
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/flashplugin-nonfree/libflashplayer.so


---

### Post by fab.head on 2008-07-15
Problem solved...


I just deleted the .opera folder in Home and flash started working again in Opera.


forestpixie, again thanks for all your support! :)

---

### Post by Elfy on 2008-07-15
Excellent - although it would be better to have not had the problem I guess ;)

An odd one to say the least, I can only imagine it was something to do with your setup; if you get the same problem with the keyboard backtrack and see what you've installed recently.

Good luck - I would say mark the thread solved - but it's not really and someone might happen across it in the future and fill in the blanks.

---

