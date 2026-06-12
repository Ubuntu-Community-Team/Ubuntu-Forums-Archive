---
title: "Terminal Listings (lines) in various colors)"
date: 2017-07-24
forum: General Help
---

### Post by Mark_in_Hollywood on 2017-07-24
While running 

ecryptfs-mount-private

the terminal returned a lot of output as the files reflect about 150 gig.

The terminal output shows some lines of the output in differing colors. (And I find the idea of a terminal color scheme quite counterproductive here.) Let me explain. I use a black text on white background. So the lines of text in the colors I'm seeing are:

black
blue
red on black background
green

What happens if, the responder to this post using a different color scheme sees my line that, in my color scheme is green, but blue in his or hers? I can only guess that the above means the same thing no matter what color scheme is used. As this relates to encryption fail, it would be nice to know what the colors meant. Try searching for keywords: 'Ubuntu terminal output colors' and see if you can find the meaning of these colored lines.

Ubuntu's pastebin does not seem to record the colors, either. Since I'm asking for help, it would be better if I could show the terminal output in it's correct color to help helpers understand.

If this is at all unclear, see as many of the attached screenshots of what the terminal shows that can fit in one post.  And if someone who can decipher the lines' colors would explain this to me, I would be grateful.

[ATTACH=CONFIG]276119[/ATTACH][ATTACH=CONFIG]276120[/ATTACH][ATTACH=CONFIG]276121[/ATTACH][ATTACH=CONFIG]276122[/ATTACH]

---

### Post by oldos2er on 2017-07-24
You probably want to search for "Ubuntu bashrc color" to find some relevant info. 

If your user's .bashrc file is set to show colors then it's behaving correctly.

---

### Post by vasa1 on 2017-07-24
You can also look at *man dir_colors* and have your very own dircolors by running```
dircolors -p > ~/.dircolors
```and then editing that file to suit your requirements.

I find colors in the terminal useful.

Commenting out```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

```from .bashrc after backing up your *.bashrc* may remove all color effects.

---

### Post by Mark_in_Hollywood on 2017-07-24
Mr. oldos2er and Mr. vasa1:

Thank you for your responses. I am trying to understand what the colors mean, not change them. Please accept my apology if I have posted so poorly that I have confused you. 

I will try again.

When the terminal output lines have color rather than black on white, does that mean something?

---

### Post by #&amp;thj^% on 2017-07-24
Sorry that would be Mrs/Miss  oldos2er just for the record. :p

---

### Post by oldos2er on 2017-07-24
Ms is fine, but plain ol' oldos2er is best. No need for formality here.

Some info here: [https://askubuntu.com/questions/466198/how-do-i-change-the-color-for-directories-with-ls-in-the-console](https://askubuntu.com/questions/466198/how-do-i-change-the-color-for-directories-with-ls-in-the-console)

---

### Post by Mark_in_Hollywood on 2017-07-25
I apologize. Names like olddos2er aren't indicative of much towards gender. I was trying to express polite gratitude. I still am. Thanks.

I do not want to change colors. I want to know whether terminal output of color represents something of a "coding" or "computer language" nature. Here is my problem, which I did not want to detail in this post, so as to avoid making two problems in one post. I'm trying to use Occam's Razor here. Simplicity over complexity.

On an install of 16.04.2, I selected to encrypt the drive, using the common encryption scheme. Something failed. When I view the encrypted files, the terminal produces several hundred lines of text. Those are represented by the screenshots I posted in #1. Most are in what I would call "normal", which in my case is black text, white background. Some few lines are in blue, one is green and two are black background and red text. 

Does red on black mean that object is a problem? Green mean about to throw up? Blue is sad? Or does colors, varying from the majority show where something isn't working?

I am not trying to change the color palette, ladies.

---

### Post by vasa1 on 2017-07-25
Did you read the links provided? Did you look at dircolors? Or does dircolors not apply to an encrypted system? I don't know :(

---

### Post by oldos2er on 2017-07-25
This is explained in the link I posted. I don't understand what encryption has to do with it, mainly because I don't use it.

---

