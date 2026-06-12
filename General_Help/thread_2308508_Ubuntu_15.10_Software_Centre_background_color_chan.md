---
title: "Ubuntu 15.10 Software Centre background color change"
date: 2016-01-03
forum: General Help
---

### Post by Novum Sanguinis on 2016-01-03
For Ubuntu 15.10 (Wily Werewolf) I hadn't been able to read the text. I narrowed the event down to when I installed a dark theme. Naturally, the background of the Software Centre stayed the off-white color while the text turned white. I managed to change the background colour fix it by doing the following.

Go to terminal and copy/paste this in:
```

gksudo gedit /usr/share/software-center/ui/gtk3/css/softwarecenter.css

```

It will open the written theme for the software center.

Locate these lines:
```
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;

```

Comment them out like so:
```

/* 
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;
*/

```

Copy/Paste these just below that:
```

@define-color light-aubergine #aa886e; /* orange-grey */
@define-color super-light-aubergine #b69780; /* kitten grey */

```

So that the finished product looks like this:

```

/* 
These are the originals
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;
*/


@define-color light-aubergine #aa886e; /* orange-grey */
@define-color super-light-aubergine #b69780; /* kitten grey */

```

And that will result in the following software centre:
[ATTACH=CONFIG]266525[/ATTACH]

---

### Post by brian-mccumber on 2016-01-03
I get my themes from noobslab and if they are dark themes the theme developer usually includes terminal commands to fix the software center. Here is what my software center looks like -
[IMG]http://americanacolyte.site50.net/usc.png[/IMG]

I do like that you figured out where to change the css colors for the software center's theme. I was doing that for the color schemes for gedit that can be installed, they are just about as easy to customize as the software center colors.

Here is a link to a dark theme for Wily which is pretty much the same as the dorian theme I use for Trusty which has the software center fix and the way to revert it back to default colors towards the bottom around the installation instructions if you would like to check it out.

[http://www.noobslab.com/2015/06/delorean-dark-theme-now-available-for.html](http://www.noobslab.com/2015/06/delorean-dark-theme-now-available-for.html)

P.S. sorry about the image size but everytime I try to upload and insert an image into a post I get logged out of the forums.

---

