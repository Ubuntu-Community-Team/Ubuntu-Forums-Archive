---
title: "Webpage as screensaver"
date: 2015-09-27
forum: General Help
---

### Post by fejoiwan on 2015-09-27
hi everyone

I'm trying to get xscreensaver to display a website. I know of a few approaches that have been done but none of them worked out for me. I tried the webkit-based webscreensaver by lmartinking:
[https://github.com/lmartinking/webscreensaver](https://github.com/lmartinking/webscreensaver)

This just made my screen black and displayed me an error message:
```
Vector smash protection is enabled
```

The webpage itself was not visible. So based on the approach using an old opera version found here:
[http://ubuntuforums.org/showthread.php?t=883823](http://ubuntuforums.org/showthread.php?t=883823)
I decided to build my own thing based on the midori browser. I edited my ~/.xscreensaver file and added:
```
"WebSaver" midori -e Fullscreen -a http://my.website.com \n\
```
under programms. It shows up in the menu but on activation the screen just turns black. However, when I move the mouse to get back to the OS, the website shows up for a very short period of time - so I guess it can't be all wrong. Besides, when i run the command in a terminal, the website shows up and works properly. The terminal is once again displaying the message
```
Vector smash protection is enabled
```

Anyone has an idea on that? I hope my approach could be useful to other people trying the same thing.

---

### Post by Bucky Ball on 2015-09-27
*Thread moved to **General Help**.*

Welcome. Why are you not using the commands given on the link in the order they are given? Under programs in your xscreensaver file:

```
webscreensaver                  \n\
```

Then set the url with:

```
-url <url_to_the_page_you_want>
```

I'm thinking your command might look more like:

```
webscreensaver \n\ -url [http://my.website.com](http://my.website.com)
```

The order might be different, but it would only be the order of the two parts of the command:

```
webscreensaver -url [http://my.website.com](http://my.website.com) \n\
```

The command in your post has no '-url' before the url address which would cause issues. Not sure if you would need the 'Fullscreen' command.

PS: Just had another look at the webscreensaver page. It is incredibly old in software terms and hasn't been maintained in three and a half years. Perhaps that's why it isn't working on a currently supported OS.

---

### Post by fejoiwan on 2015-09-27
As I said, I tried using webscreensaver. I used it with
```
webscreensaver -url http://my.website.com \n\
```

This just turned my screen black with a little yellow message in the top left corner stating
```
Vector smash protection is enabled
```

And yes, I saw the age. That's partially why I decided to try an approach based on the Midori browser - since the approach based on Opera was very old too and the current version of Opera is not supporting the needed switches.

---

### Post by Bucky Ball on 2015-09-27
Then try the other way:

```
webscreensaver \n\ -url http://my.website.com
```

That is the order they come on the link.

Doesn't matter what browser you use, it is still three and a half years advanced from last time this relic got some TLC. Midori now is Midori 2015, not 2012. :)

Good luck with it and hope someone has some ideas.

---

### Post by fejoiwan on 2015-09-27
Just to clarify: The approach with midori is competely separate from webscreensaver - which I try not to use at all because of it's age.

---

### Post by Bucky Ball on 2015-09-27
Ah ha. Sorry about that. I'll take a look. :)

* Looked. An even older method. Once again, good luck with it. :)

---

### Post by fejoiwan on 2015-09-27
I looked a little further and found a solution I can live with. Using a screenlet as described in
[http://askubuntu.com/questions/26017/active-web-site-as-gnome-background](http://askubuntu.com/questions/26017/active-web-site-as-gnome-background)
is not exactly as pretty but doing the job from me. Thanks for your time!

---

### Post by Bucky Ball on 2015-09-27
Well done, all good and thanks for marking as solved.

Enjoy the forums and the OS. :)

---

