---
title: "Corrupt labels in LibreOffice"
date: 2016-05-28
forum: General Help
---

### Post by omar-ahafez87 on 2016-05-28
Dear Ubuntu Community,

I recently made the decision to make a clean installation of Ubuntu 16.04 on my Toshiba SATELLITE-M50D-A laptop. However, as I opened LibreOffice and started setting it up, I noticed that some parts are not rendered correctly. I honestly find it hard to describe my problem in words, so please look at the screenshot attached below to have a better idea.

I am honestly perplexed and have no idea why this happens or how to fix it.

Any help, please? :(

[http://i.imgur.com/C6HlRkj.png](http://i.imgur.com/C6HlRkj.png)

---

### Post by wildmanne39 on 2016-05-28
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

---

### Post by izznogooood on 2016-05-28
What kind of Graphics card do you have?

---

### Post by omar-ahafez87 on 2016-05-28
> **izznogooood said:**
> What kind of Graphics card do you have?

I have a Gallium 0.4 on AMD KABINI (DRM 2.43.0, LLVM 3.8.0).

---

### Post by omar-ahafez87 on 2016-05-28
> **Wild Man said:**
> Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

Note taken. 

Sorry for the inconvenience. :)

---

### Post by izznogooood on 2016-05-28
You might want to change your topic and include AMD graphics. There are issues with this but I have Nvidia so I have no reference.

---

### Post by omar-ahafez87 on 2016-05-28
> **izznogooood said:**
> You might want to change your topic and include AMD graphics. There are issues with this but I have Nvidia so I have no reference.

The weird thing is that this problem seems to show up only in Libreoffice. The rest of the programs or windows on the system seem to render just fine..!

How so..? :/

---

### Post by vasa1 on 2016-05-28
> **omar-ahafez87 said:**
> The weird thing is that this problem seems to show up only in Libreoffice. The rest of the programs or windows on the system seem to render just fine..!

How so..? :/
What do you see when you launch LibreOffice from a terminal? Any messages, warnings, etc?

What do you see when you run```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```replacing "calc" with "writer" or any other suite component?

And have you tried a [new profile]("https://wiki.documentfoundation.org/UserProfile")?

---

### Post by omar-ahafez87 on 2016-05-29
> **vasa1 said:**
> What do you see when you launch LibreOffice from a terminal? Any messages, warnings, etc?

What do you see when you run```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```replacing "calc" with "writer" or any other suite component?

And have you tried a [new profile]("https://wiki.documentfoundation.org/UserProfile")?

When I ran the command you mentioned, I had the following result:

```
omar@omar-SATELLITE-M50D-A:~$ SAL_USE_VCLPLUGIN=gtk libreoffice --writer
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 42 (X_SetInputFocus)
  Resource id:  0x5800b6e
```

There seems to be and error of some kind, as you can see. :\

And what do you mean by "a new profile"?



[UPDATE]

I just ran the same command again (SAL_USE_VCLPLUGIN=gtk libreoffice --writer) and it ran with no error.

But the problem with Libreoffice still persists..

---

### Post by DuckHook on 2016-05-30
This is a known bug and affects my install as well. Please see the following link:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1581522](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1581522)

...and notify the developers that it affects you as well using the up-vote notification near the top of page. You will need a LaunchPad acct to do so, but bug reports help out the community.

---

### Post by omar-ahafez87 on 2016-05-30
> **DuckHook said:**
> This is a known bug and affects my install as well. Please see the following link:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1581522](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1581522)

...and notify the developers that it affects you as well using the up-vote notification near the top of page. You will need a LaunchPad acct to do so, but bug reports help out the community.

Thank you, DuckHook. I just did as you advised.

Let's hope some solution comes up soon.

---

### Post by DuckHook on 2016-05-30
> **omar-ahafez87 said:**
> Let's hope some solution comes up soon.+1

In the meantime, it is more an annoyance than a real problem. You can recycle the dialogue box by closing down LibreOffice and opening it again. Often this will clear the garbling and you can see the dialogue content. You will see this same garbling inside the options dialogues when trying to change your global settings. Just switch to a different settings page, then switch back, and the the proper content will usually be repainted over the garble.

---

### Post by vasa1 on 2016-05-30
@DuckHook, do you have the same sort of graphics that OP has?

I have very basic graphics, Intel integrated, no GPU. And I don't see any garbling anywhere.

In *Tools > Options > LibreOffice > View > Graphics Output* I have everything unticked.

And in *Tools > Options > LibreOffice > OpenCL*, I have only the first option ticked. (I think that was the default).

And have you tried changing themes?

Of course, none of this should be necessary but ...

Edit: just saw OP's mention that Kubuntu shows the same issue. So that would rule out themes.

---

### Post by vasa1 on 2016-05-30
BTW, two more related bugs?

[URL="https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1569566"]
Missing / garbled fonts in LibreOffice Calc[/URL]

[font glyph corruption on dialog box]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1575000")

---

### Post by DuckHook on 2016-05-30
Thanks, vasa1 but that was the first thing I thought of too. Aside from both being AMD, they are quite different. Mine is a Tahiti HD 7950, his is a Kabini. Of course, it probably does have something to do with both being AMD, and some obscure LibreOffice thing, but just like OP, mine only affects LibreOffice and no other app. Moreover, it's only dialogue boxes and not docs so is not really too debilitating. More annoying than anything else.

---

### Post by DuckHook on 2016-05-30
> **vasa1 said:**
> BTW, two more related bugs?Thanks for those. Highly probable they are same cause. Wouldn't want to think I was seeing things. :eek:

---

### Post by omar-ahafez87 on 2016-05-30
> **vasa1 said:**
> BTW, two more related bugs?

[URL="https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1569566"]
Missing / garbled fonts in LibreOffice Calc[/URL]

[font glyph corruption on dialog box]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1575000")


In one of these bug reports you mentioned, it is said that the upcoming version of LibreOffice (currently in alpha phase) has this problem solved and no garbled elements have been found.

I really hope that this is the case..

But as DuckHook said, the issue is more annoying than anything else.

---

### Post by DuckHook on 2016-08-11
Finally, after months of living with corrupted fonts, the solution is to install the Libreoffice PPA and upgrade to v.5.2. Instructions as follows:```
sudo add-apt-repository ppa:libreoffice/ppa
``````
sudo apt update
```Next (*IMPORTANT*) an old library must be removed so as not to conflict:```
sudo apt remove libreoffice-gtk
```Now, the newest Libreoffice can be installed with:```
sudo apt dist-upgrade
``````
sudo apt install libreoffice-gtk2 libreoffice-gnome
```Above instructions are from this link: [http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa](http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa)

I had not realized how debilitating this problem would prove to be when I originally posted. Corrupted fonts are more than an inconvenience since it renders some dialogue boxes completely unreadable. My workaround until now was to use Libreoffice in a Xubuntu/Lubuntu VM which bypasses the GTK/AMD combination video bug which appears to be the cause of the problem. But with v.5.2, this workaround is thankfully no longer necessary.

I shall leave it to the OP to mark this problem "solved" and if s/he is no longer subscribed to this thread, I shall mark it so in 24 hrs.

---

