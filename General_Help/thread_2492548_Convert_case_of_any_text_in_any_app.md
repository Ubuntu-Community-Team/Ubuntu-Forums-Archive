---
title: "Convert case of any text in any app"
date: 2023-11-14
forum: General Help
---

### Post by lucmorizur on 2023-11-14
Hi everyone;

this thread follows [this (old) one ("Convert lower to upper case etc.")]("https://ubuntuforums.org/showthread.php?t=1176205") opened in 2009.

The following sentence shows my initial problem. uNFORTUNATELY i SOMETIMES TYPE TEXT WITH CAPS LOCKED BY MISTAKE. I *can* type while looking at the screen rather than the keyboard, but I'm then far less efficient, I produce more typos, it requires more attention... well I usually type looking at my keyboard. And sometimes after having finished my sentence, I'm crying when I understand that I have to re-type the whole text. Of course sometimes it happens within an app which can handle text case, but often this is available via menus requiring several clicks; and "swap case" is almost never available, so you still have to do corrections — well, it's faster to re-type.

Thus of course I was dreaming of a keyboard shortcut so to swap the case of the mistyped text, and available anywhere. Below how I could implement that.

The solution is based on software [Autokey]("https://github.com/autokey/autokey"). The provided link is the project on Github, but as far as I remember the app can be installed a very usual way. It may have two different versions (Qt or GTK+) whether you're using Gnome, or KDE, Lubuntu...

Once it is installed, you need to get [Python script "stringcase"]("https://pypi.org/project/stringcase/"). There's a very fast way to so:
```
$ pip install stringcase
```
Of course if "pip" command returns an error, then you have to install Python, but as far as I know, Python is installed by default on GNU/Linux.

Unfortunately, the script doesn't include the "swap case" procedure :|. It is still interesting though, as it includes many other procedures you may find interesting. Anyway to add the procedure in the script, just find out where the script has been loaded:
```
$ sudo find / -iname "*stringcase*" -type f
```
(Let's use below [FONT=courier new][COLOR=#000000]/stringcase_path/stringcase.py[/COLOR][/FONT] for the original script file path; of course, you'll have to replace each time "[FONT=courier new]/stringcase_path/[/FONT]" with the path you found just before.)
Make a backup copy of this file:
```
$ sudo cp /stringcase_path/stringcase.py /stringcase_path/stringcase.py.ori
```
This way we're safer; and let's do also a working copy of the script, which you will safely edit:
```
$ sudo cp /stringcase_path/stringcase.py $HOME/stringcase_work.py
```
Let's make your file editable:
```
$ sudo chown $USER:$USER stringcase_work.py
$ chmod ug+rw stringcase_work.py
```
Now you can edit the script with your favourite text editor. At the end of the file, add:
```
def swapcase(string):
    """Swap case

    Args:
        string: String to convert.

    Returns:
        string: String with case swapped.

    """
    return str(string).swapcase()

```
Save the file and make it replace the original file:
```
$ sudo cp $HOME/stringcase_work.py /stringcase_path/stringcase.py
```
That's it!
Now is time to set up Autokey. Just run it; and maybe you should play a little bit with it so to learn how it works. Anyway the software proposes two features: phrases and scripts. Here we're interested in creating a new script, named "Choose case" for instance, which you can add in any "folder" Autokey offers, or that you would create also. The important is that it is a *script* that you create finally.
For this script I was inspired by [one proposed by Omri Caspi]("https://gist.github.com/caspx/7aee77572f6501897d3cb84900399abb"), many thanks to him; but unfortunately here also some corrections are needed. Anyway as for now, you can copy/paste his script in the script area you have for your brand new "Choose case" script in Autokey. You should notice that this editing area applies syntax colouring, which is quite handy.
And now the corrections: the following
```
ret_code, choice = dialog.list_menu(choices,
                                    title=phrase,
                                    text='Select Case',
                                    height="500",
                                    width="200")

```
Must be replaced by
```
ret_code, choice = dialog.list_menu(choices,
                                    title=phrase,
                                    message='Select Case')

```
(The "text" variable name is replaced by "message"; and the specifications for height and width of the list unfortunately would make the list not pop up :cry:.)
And a last correction: in the list of case conversion proposed, add the swapcase...:
```
choices = [
    'camelcase',
    'capitalcase',
    'constcase',
    'lowercase',
    'pascalcase',
    'pathcase',
    'sentencecase',
    'snakecase',
    'spinalcase',
    'titlecase',
    'trimcase',
    'uppercase',
    'swapcase',
    'alphanumcase']

```
(In the code above, I have put it at the penultimate position.)

Now you just need to set up a shortcut key thanks to Autokey for this script (I had difficulties in setting [FONT=courier new]<super>+a[/FONT]; if so, you can save, exit Autokey (make sure you allow the Autokey taskbar icon in the preferences, and right-clik on it so to fully exit), and edit the .json file in $HOME/.config/autokey/data/(...) which corresponds to your script), and, well, normally speaking that's all! You should now be able to select a sentence in any text-typing app, and convert it as chosen thanks to the keyboard shortcut you have set up :cool:!

Of course you see it's very easy to adapt the scripts to your need: as for me, I made a shortcut only dedicated to swapcase, I thus don't need to select it in the list, it's applied immediately. And I made another shortcut (and another script) proposing a list, but with far less stuff, only the ones I shall use.

Please tell if something is not clear; and enjoy!

---

### Post by dragonfly41 on 2023-11-14
AutHotKey is a nice tool. But there is an easier route apparently (I've just looked it up) using xdotool.

[https://www.cyberciti.biz/faq/linux-deactivate-caps-lock/](https://www.cyberciti.biz/faq/linux-deactivate-caps-lock/)

This does not convert, but blocks it happening in error *before* you start typing in CAPS.

---

### Post by The Cog on 2023-11-14
You could put this is a file ~/bin/capslock and make it executable. Then just type "capslock on" or "capslock off". Again, it doesn't convert text, just enables or disables the capslock button.
```
#!/bin/bash
[ "$1" == on ] && setxkbmap -option
[ "$1" == off ] && setxkbmap -option caps:none
```

---

### Post by MAFoElffen on 2023-11-14
You already have most of that in the Generic Hotkeys of Windows and Linux with:
<Cntrl><K>, then <Cntrl><U> to convert selected to uppercase.
<Cntrl><K>, then <Cntrl><L> to convert selected to lowercase.

For MAC those are:
<Cmd><K>, then <Cmd><U> to convert selected to uppercase.
<Cmd><K>, then <Cmd><L> to convert selected to lowercase.

Then, if you need more detail beyond that, you can setup keyboard macro's using Python, if you use libraries pyinput, pyautogui, and caseconverter... With the combination of using those, you can setup hotkeys and define what you want triggered to convert the selected text to whatever...

You can also set up autoreplace macros, to autofill text variables... Like for example, your full name, email address, street address, disclaimers, program headers (as a template), etc.

---

### Post by vanadium on 2023-11-15
> **MAFoElffen said:**
> You already have most of that in the Generic Hotkeys of Windows and Linux with:
<Cntrl><K>, then <Cntrl><U> to convert selected to uppercase.
<Cntrl><K>, then <Cntrl><L> to convert selected to lowercase.

I am not sure whether this is generic in Linux. In Gedit, <Ctrl><U> and <Ctrl><L>  convert to uppercase and lowercase, but elsewhere this will depend on if or how the application uses the shortcut keys.

To rather "universily"  convert to lowercase, you can work with a chained command invoked through a system wide shortcut key. To simulate keyboard presses, you want to use ydotool, which works on both Xorg and Wayland. xdotool works on Xor only:

```
sh -c "sleep 0.3 && wl-paste -n -p | PERLIO=:utf8 perl -pe '$_=lc' | wl-copy && ydotool key 42:1 110:1 110:0 42:0"
```

The selected text is pasted from the primary clipboard into (in this case) perl, which changes it to lower case. Then the processed text is placed on the (secondary) clipboard and pasted back using <Ctrl><V>. A "sleep" command is needed to allow time to release the shortcut key.

---

### Post by TheFu on 2023-11-15
And here, I've been using **tr** for the last 3 decades.  Didn't realize I was doing it the hard way.  er ... or not.

```
NAME
       tr - translate or delete characters
```

```
$ tr '[:lower:]' '[:upper:]'
```
[https://linuxize.com/post/linux-tr-command/#convert-lower-case-to-upper-case](https://linuxize.com/post/linux-tr-command/#convert-lower-case-to-upper-case)

Oh, sorry, you need
```
$ tr  '[:upper:]'  '[:lower:]'
```

---

### Post by vanadium on 2023-11-15
Certainly the lighter way, but I also needed scripts to convert to sentence case, and to title case, so I ended up a bit heavier (not my own findings, for sure). Looking to the link you gave, there definitely is much more that can be done with "tr" than I taught.

---

### Post by TheFu on 2023-11-15
There's usually 50, if not 500, possible solutions. Each has a place, but I find that new Linux converts often don't know about the 50 yr history and all the tools that have been around nearly that long which are tiny and handle a specific task nicely.

---

### Post by MAFoElffen on 2023-11-15
> **TheFu said:**
> There's usually 50, if not 500, possible solutions. Each has a place, but I find that new Linux converts often don't know about the 50 yr history and all the tools that have been around nearly that long which are tiny and handle a specific task nicely.
LOL. Look how many were written for Emacs. I used to live in Emacs many, many years ago.

---

