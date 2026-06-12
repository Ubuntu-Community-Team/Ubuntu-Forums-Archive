---
title: "My Conky Setup (and utilities) with files"
date: 2013-09-08
forum: General Help
---

### Post by HiImTye on 2013-09-08
I haven't updated my conky setup on here for a while, so I thought I'd update them. here's what it looks like:
[https://www.facebook.com/photo.php?fbid=10151567316421502&l=436f785e5a](https://www.facebook.com/photo.php?fbid=10151567316421502&l=436f785e5a)

[COLOR=#000080][SIZE=4]Basic[/SIZE][/COLOR]
to get things going, place the files in [COLOR=#008000]*~/Launchers*[/COLOR]  (or place   them wherever, but you'll have to edit them to accomodate  your other   location). this should make them 95% functional. there's a  few things   you'll need to do to finish off:
[B]
for non-nvidia GPUs (or nvidia GPU with non-proprietary driver):[/B]

[LIST]
[*]delete the line in [COLOR=#008000]*.tconk-config-cpu*[/COLOR]```
${color2}GPU: ${alignr}${color3}${nvidia temp}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C
``` 
[/LIST]
 (make sure that you don't leave a blank line, or you'll have one in your display)

**to get Facebook's notifications working:**

[LIST]
[*]download the Firefox plugin [here]("https://addons.mozilla.org/en-us/firefox/addon/export-cookies/") 
[*]make sure Facebook is logged in inside FF, and that it is set to stay logged in across sessions 
[*]go to [COLOR=#ff8c00]*Tools > Export Cookies...*[/COLOR] 
[*]save the file as [COLOR=#008000]*~/Launchers/cookies.txt*[/COLOR] 
[*]run the following script 
[/LIST]
```
cd $HOME/Launchers
grep ^.facebook.com [COLOR=#008000]cookies.txt[/COLOR] > .tconk-settings-fbCookies
rm cookies.txt
```

**to get GMail's notifications working:**
 
[LIST]
[*]edit [COLOR=#008000]*~/Launchers/.tconk-settings-accountInfo*[/COLOR] 
[*]enter your account information and save the file (NOTE: this information is stored in plain text. [here]("http://plaintextoffenders.com/about/")'s an article about the dangers of storing passwords in plain text) 
[/LIST]
 
**to add a new custom resolution set:**
[LIST]
[*]copy [COLOR=#008000]*.tconk-settings-display-default*[/COLOR] to a new file with your desired display resolution and edit the values inside, like: 
[/LIST]
```
cd $HOME/Launchers
cp [COLOR=#008000].tconk-settings-display-default[/COLOR] [COLOR=#008000].tconk-settings-display-[/COLOR][COLOR=#a52a2a]*1024x768*[/COLOR]
```
[LIST]
[*]edit [COLOR=#008000]*tconk.sh*[/COLOR] and create a new resolution set:
[LIST]
[*]after [COLOR=#ff8c00]*OPTION2*[/COLOR], add a new one (i.e. [COLOR=#ff8c00]*OPTION3*[/COLOR]) 
[*]copy the [COLOR=#ff8c00]*elif*[/COLOR] line for [COLOR=#ff8c00]*OPTION2*[/COLOR], and the [COLOR=#ff8c00]*line that follows it*[/COLOR] 
[*]paste them before [COLOR=#ff8c00]*else*[/COLOR] 
[*]change [COLOR=#ff8c00]*2*[/COLOR] to your new number, and the resolution at the end of the second copied line. you should now have a section that resembles something like this: 
[/LIST]
            
[/LIST]
```
OPTION1="1920x1080"
OPTION2="1360x768"
[COLOR=#a52a2a]*OPTION3="1024x768"*[/COLOR]
if [ "$DIMENSIONS" = "$OPTION1" ]; then
 . "$HOME/Launchers"/.tconk-settings-display-1920x1080
elif [ "$DIMENSIONS" = "$OPTION2" ]; then
 . "$HOME/Launchers"/.tconk-settings-display-1360x768
[COLOR=#a52a2a][I]elif [ "$DIMENSIONS" = "$OPTION3" ]; then
  [/I]*. *[/COLOR][COLOR=#008000]*"$HOME/Launchers"/.tconk-settings-display-1024x768*[/COLOR]
else
 echo "no settings specified for the range dimensions=$DIMENSIONS"
 . "$HOME/Launchers"/.tconk-settings-display-default
fi
```

[COLOR=#000080] [SIZE=4]Advanced Usage[/SIZE][/COLOR]
**delaying launch**:
[LIST]
[*]to launch with a delay, simply add an argument to [COLOR=#008000]*tconk.sh*[/COLOR] when you run it, i.e.```
$HOME/Launchers/tconk.sh 1
```this is useful for when you first log in, to give your window manager, etc, time to load before conky does. 
[/LIST]
 **customization:**
[LIST]
[*]I've commented all of the files extensively, to make editing them easy. the only exceptions are the actual conky config files, as commenting the actual displays is impossible. 
[/LIST]
 
[COLOR=#000080][SIZE=4]Extras[/SIZE][/COLOR]
the extras package includes some extra files that [COLOR=#008000]*tconk.sh*[/COLOR] calls (if they exist). this includes:
[LIST]
[*]a 'startup tasks' shell script that launches certain programs, removes certain files that aren't needed, and runs the 'sound system' script 
[*]a 'sound system' script that switches out the *[COLOR=#008000].asoundrc[/COLOR]* file (and launches PulseAudio if necessary) according to whichever sound system is specified. I use this for gaming, mostly, or when I'm done gaming. some configs included 
[*]a 'gnome shell' script that checks if Gnome-Shell is running, and if not, launches it. useful for if your GS crashes. 
[/LIST]

---

### Post by HiImTye on 2013-09-08
not sure why the post is so messed up, must be an issue with the formatting editor (it did mess up while I was writing the post). tried editing to fix it, but no cigar

---

### Post by coffeecat on 2013-09-08
There was a single misplaced [/code] tag where you were nesting a code box within a bullet list, which seems to have had a dramatic knock-on effect on the rendering of the whole page. Fixed now, but it took some finding! :) If you hover and mouse-click over "Last edited by" you can see the whole edit history and the exact changes.

---

### Post by HiImTye on 2013-09-08
thanks, I wasn't sure. it's because the editor adds [/code] and [code] tags to any code blocks that don't terminate on the same bulleted line. kind of annoying, since I had to remove the multi-line code blocks from the bullets, but I'll know for the future ;)

---

