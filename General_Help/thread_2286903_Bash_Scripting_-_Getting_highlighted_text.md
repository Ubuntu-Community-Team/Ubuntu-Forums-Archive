---
title: "Bash Scripting - Getting highlighted text"
date: 2015-07-15
forum: General Help
---

### Post by cowboy.bebop on 2015-07-15
Is there a script or command the allows for obtaining the highlighted text in terminal like the cyan highlighted part in this screenshot?

idk: read <highlightedtext> var

[[img]http://i.imgur.com/u98vqsum.png[/img]](http://imgur.com/u98vqsu)

---

### Post by QDR06VV9 on 2015-07-15
Here is a start If I understand.
[URL="http://www.pixelbeat.org/docs/terminal_colours/"]http://www.pixelbeat.org/docs/terminal_colours/
[/URL]
And This
 Use ack. Checkout its --passthru option here: [ack]("https://metacpan.org/pod/ack")
  You can also do it using grep like this:
  ```
$ grep --color -E '^|pattern1|pattern2' file name
```
  Or this:
  ```
$ command_here | grep --color -E '^|pattern1|pattern2'
```
  This will match all lines and highlight the patterns. The ^ matches every start of line, but won't get printed/highlighted since it's not a character.
  (Note that most of the setups will use --color by default. You may not need that flag).
Or if you are talking about copying the the highlighted text, Highlight the text you want with the cursor or mouse, Then use this key combo<ctrl+shift+c> to copy.
Then to paste back into the terminal you would use key combo <ctrl+shift+v> to paste.
     

Regards

---

### Post by sudodus on 2015-07-15
+1

ANSI sequences work well for colours or inverse video highlighting.

example:
```

inversvid="\0033[7m"
resetvid="\0033[0m"

/bin/echo -e "$inversvid Hello World $resetvid"

```

---

### Post by cowboy.bebop on 2015-07-15
> **runrickus said:**
> Here is a start If I understand.
[URL="http://www.pixelbeat.org/docs/terminal_colours/"]http://www.pixelbeat.org/docs/terminal_colours/
[/URL]
And This
 Use ack. Checkout its --passthru option here: [ack]("https://metacpan.org/pod/ack")
  You can also do it using grep like this:
  ```
$ grep --color -E '^|pattern1|pattern2' file name
```
  Or this:
  ```
$ command_here | grep --color -E '^|pattern1|pattern2'
```
  This will match all lines and highlight the patterns. The ^ matches every start of line, but won't get printed/highlighted since it's not a character.
  (Note that most of the setups will use --color by default. You may not need that flag).
Or if you are talking about copying the the highlighted text, Highlight the text you want with the cursor or mouse, Then use this key combo<ctrl+shift+c> to copy.
Then to paste back into the terminal you would use key combo <ctrl+shift+v> to paste.
     

Regards

I am not referring to copy+paste with a mouse, I meant programatically copy the highlighted text.

> 
ANSI sequences work well for colours or inverse video highlighting.

example:
Code:
inversvid="\0033[7m"
resetvid="\0033[0m"

/bin/echo -e "$inversvid Hello World $resetvid"


So it is only possible to highlight text by scripting it, but not copy whats already been highlighted via mouse input?

---

### Post by QDR06VV9 on 2015-07-15
> So it is only possible to highlight text by scripting it, but not copy whats already been highlighted via mouse input?
Not trying to sound harsh here but could you ask a clear question?(Specific)

---

### Post by cowboy.bebop on 2015-07-15
> **runrickus said:**
> Not trying to sound harsh here but could you ask a clear question?(Specific)

I know your not being harsh and I would hate for you to think I was ill tempered when I said that.

When you highlight in terminal, you can middle+mouse click which will paste into the command prompt whats been highlighted. Rather than physically using the middle+mouse click to paste, is it possible for someone to inherit the string thats already been highlighted by the mouse? 

In c# a user can grab from the clipboard and paste it, but the clipboard appears to be a global feature in c#; where as terminal, middle mouse click will paste whats has been physically highlighted by the user, but will not paste outside of terminal. Is it possible to mimic the middle mouse click in bash scripting?

---

### Post by sudodus on 2015-07-15
You can high-light text (using the left mouse button) and you can paste it (by clicking on the middle mouse button) into another terminal window or into a text editor or other program that accepts text input.

If this is not what you want, please describe what you want.

Edit: We were posting at the same time. Now I know, and I am sorry, I have no solution for your problem. Maybe (only maybe) you can use ***xsel*** or ***xdotool***

---

### Post by QDR06VV9 on 2015-07-15
> **Ubuntwha said:**
> I know your not being harsh and I would hate for you to think I was ill tempered when I said that.
Nothing of the sort:D I just had problems understanding how to answer with out coming across gruff.(Lost in Translation):confused: 

> **sudodus said:**
> You can high-light text (using the left mouse button) and you can paste it (by clicking on the middle mouse button) into another terminal window or into a text editor or other program that accepts text input.

If this is not what you want, please describe what you want.

Edit: We were posting at the same time. Now I know, and I am sorry, _I have no solution for your problem. Maybe (only maybe) you can use ***xsel***_
+1

---

### Post by cowboy.bebop on 2015-07-15
XSel is exactly what I am looking for, ty guys so much! =)

---

### Post by sudodus on 2015-07-15
Good luck with xsel, and let us know, if you find a solution, and in that case, please share it (with details) :-)

---

### Post by cowboy.bebop on 2015-07-15
xsel did in fact work, however i was too blind to see a solution already in front of me and had nothing to with highlighting. Apparently you can just ```
nautilus .
``` of the pwd and it opens to in the gui. I did not know this. However xsel works great when catting files that contain directory information one could easily ```
xsel -c | ls -a
``` to list the files of the highlighted directory from the cat.

Was a pleasure learning this and as always, thank you for everyone's help ;)

---

### Post by sudodus on 2015-07-15
I'm glad you found a solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

