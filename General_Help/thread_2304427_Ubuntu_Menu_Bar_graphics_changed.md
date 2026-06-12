---
title: "Ubuntu Menu Bar graphics changed"
date: 2015-11-26
forum: General Help
---

### Post by black_skully on 2015-11-26
Hi, I'm new to Ubuntu, and I am wondering why the menu bar on my lock screen has different graphics than the one after I login.

in the login/lock screen:
[ATTACH=CONFIG]265784[/ATTACH]

after I login:
[ATTACH=CONFIG]265785[/ATTACH]

I don't know if a program caused this (I have a few things installed on it, incl. Unity Tweak Tool for example).

any help how can I get this weird one back to normal?

EDIT:
I also have Cairo-Dock but no settings for it there also..

EDIT II:
As I mentioned in  a reply, if I choose 'Lock' instead of 'Log Out', they show normally and don't change!

Thank's in advance!

---

### Post by Ricardo_Velasco on 2015-11-26
Greeting:

Well as you please explain to me that package installed .

Then try uninstalling the package try :

> sudo apt-get remove --auto-remove unity- tweak -tool

To remove the package and dependencies.

or

Remove only the package

> sudo apt-get remove unity-tweak-tool


And then to remove settings


> sudo apt-get purge unity-tweak-tool

After you install the package to see if that was the problem


Or you can double check your settings Unity Tweak

I am sending you some pictures of AskUbuntu extracted for you to coax and see if you have to change the window theme Unity:


[IMG]http://i.stack.imgur.com/vVwdO.png[/IMG]




[IMG]http://i.stack.imgur.com/Tn3lZ.png[/IMG]




Thank you

---

### Post by black_skully on 2015-11-26
I tried resetting some settings to default,but I don't think unity-tweak-tool caused this, because I just noticed: if I log out, these icons change on the logon screen, but if I choose 'Lock' instead of 'Log Out', they show normally and don't change!

---

### Post by deadflowr on 2015-11-27
Open a terminal and run this
```
gsettings get com.canonical.unity-greeter icon-theme-name
```
what does it output?
You might also try running the command with the reset option inplace of the get option like
```
gsettings reset com.canonical.unity-greeter icon-theme-name
```
which should reset it to the default, which should be ubuntu-mono-dark, which is what the logged in screen is (in the screenshot)

---

### Post by black_skully on 2015-11-27
> **deadflowr said:**
> Open a terminal and run this
```
gsettings get com.canonical.unity-greeter icon-theme-name
```
what does it output?
You might also try running the command with the reset option inplace of the get option like
```
gsettings reset com.canonical.unity-greeter icon-theme-name
```
which should reset it to the default, which should be ubuntu-mono-dark, which is what the logged in screen is (in the screenshot)

So it said 'default' and after using the second command, was still 'default'

---

### Post by deadflowr on 2015-11-27
> **black_skully said:**
> So it said 'default' and after using the second command, was still 'default'
default is not what it should say.
It should say ubuntu-mono-dark.
(ubuntu-mono-dark is the default)
So try setting it with
```
gsettings set com.canonical.unity-greeter icon-theme-name 'ubuntu-mono-dark'
```

---

### Post by black_skully on 2015-11-27
> **deadflowr said:**
> default is not what it should say.
It should say ubuntu-mono-dark.
(ubuntu-mono-dark is the default)
So try setting it with
```
gsettings set com.canonical.unity-greeter icon-theme-name 'ubuntu-mono-dark'
```

'ubuntu-mono-dark' is the result now, but nothing has changed after I logged out! :\ it's really weird..

---

### Post by Ricardo_Velasco on 2015-11-28
Hello:

Here try these commands to you restarure Unity settings but first of all, before you close the session and next to your user name you select the option 'Ubuntu 2D'

I sent a picture for you to inform yourself


[IMG]http://elblogdeliher.com/wp-content/uploads/2015/01/login-en-ubuntu.jpg[/IMG]


The curious thing about this picture that I found was the bar that has the same image that you showed me your computer

Then it may be by Cairo -Dock , then uninstall it as a first step by Synaptic

If you do not anyway , try to follow these steps to restore Unity


After putting in 2D Ubuntu.

You go to the terminal and put :

> gconftool-2 --recursive-unset /apps/compiz-1

> gconftool-2 --recursive-unset /apps/compizconfig-1

And after:

> unity --reset

If you ever stayed put former Unity settings :

> rm -rf ~/.config/compiz-1/compizconfig/*


And to restore Gnome run this command :

> sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity


Try these commands : if you do not succeed then goes on to comment ..


For further questions do not forget to give your version of Ubuntu

Thank you

---

### Post by deadflowr on 2015-11-28
well, it's pre-compiz.

I think I understand it, somewhat.
OP:
open a text editor (gedit on Ubuntu) and go to open and you''ll need to go throught the main file system,
so either look for "file system" or Computer listed in the left-side-panel area.
In Computer go to usr, then go to share, then go to glib-2.0 then finally schemas.
In schemas, look for the file marked com.canonical.unity-greeter.gschema.xml

^^Alternately, and easier is to open a terminal and run
```
gedit /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
in this file look for the section marked icon-them-name
it should looks like this:
```
<key name="icon-theme-name" type="s">      
<default>'ubuntu-mono-dark'</default>
<summary>Icon theme to use</summary>
</key>
```
But i think it might look like this
```
<key name="icon-theme-name" type="s">      
<default>'gnome'</default>
<summary>Icon theme to use</summary>
 </key>
```
Note the change of the default, yours might be yet another icon set, so...
Is my thinking correct on this?

---

### Post by black_skully on 2015-11-30
> **Ricardo_Velasco said:**
> Hello:

Here try these commands to you restarure Unity settings but first of all, before you close the session and next to your user name you select the option 'Ubuntu 2D'

I sent a picture for you to inform yourself


[IMG]http://elblogdeliher.com/wp-content/uploads/2015/01/login-en-ubuntu.jpg[/IMG]


The curious thing about this picture that I found was the bar that has the same image that you showed me your computer

Then it may be by Cairo -Dock , then uninstall it as a first step by Synaptic

If you do not anyway , try to follow these steps to restore Unity


After putting in 2D Ubuntu.

You go to the terminal and put :





And after:



If you ever stayed put former Unity settings :




And to restore Gnome run this command :




Try these commands : if you do not succeed then goes on to comment ..


For further questions do not forget to give your version of Ubuntu

Thank you
Hi, my Ubuntu version is the latest (14.04).
In that list I do not have '2D Ubuntu', I have either 'Cairo-Dock (GNOME)' or 'Ubuntu (Default)', which is the default one.


> **deadflowr said:**
> well, it's pre-compiz.

I think I understand it, somewhat.
OP:
open a text editor (gedit on Ubuntu) and go to open and you''ll need to go throught the main file system,
so either look for "file system" or Computer listed in the left-side-panel area.
In Computer go to usr, then go to share, then go to glib-2.0 then finally schemas.
In schemas, look for the file marked com.canonical.unity-greeter.gschema.xml

^^Alternately, and easier is to open a terminal and run
```
gedit /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
in this file look for the section marked icon-them-name
it should looks like this:
```
<key name="icon-theme-name" type="s">      
<default>'ubuntu-mono-dark'</default>
<summary>Icon theme to use</summary>
</key>
```
But i think it might look like this
```
<key name="icon-theme-name" type="s">      
<default>'gnome'</default>
<summary>Icon theme to use</summary>
 </key>
```
Note the change of the default, yours might be yet another icon set, so...
Is my thinking correct on this?

Hi, I tried opening it, and it actually is how you mentioned it should look like..

I'm not planning to uninstall Cairo-Dock or Unity Tweak Tool at the moment, but can for sure change any of their settings, if it is the problem :\

thank's for your replies guys.

---

