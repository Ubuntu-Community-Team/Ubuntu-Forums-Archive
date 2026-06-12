---
title: "I updated the computer and the headers and right click menus are dark!"
date: 2013-10-12
forum: General Help
---

### Post by sdowney717 on 2013-10-12
And I cant stand it.
The browser icons also have changed.

How can I get it to go back the way it was?
Which WAS the default, it is like a theme has been forced on me.

pic shows on chrome the dark gray top bar.
it does the same in firefox.
[IMG]https://lh4.googleusercontent.com/-2B-yebbgbcA/Ulk6LjQ4uCI/AAAAAAAAFiI/-iQ2IhY9sMg/s1440/Screenshot%2520from%25202013-10-12%252007%253A58%253A26.png[/IMG]

look at how ugly this looks. very dark blocky lines
[IMG]https://lh6.googleusercontent.com/-nqG8inwLS4A/Ulk7C67pCvI/AAAAAAAAFig/RjpV6D-ZnXE/s1280/Screenshot%2520from%25202013-10-12%252008%253A05%253A05.png[/IMG]

---

### Post by sdowney717 on 2013-10-12
This solved the problem
[http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values)

```
gconftool-2 --recursive-unset /apps/compiz-1

unity --reset &

rm -rf .gnome .gnome2 .gconf .gcond .metacity

Then, restart PC

NEXT TIME: install 'Ubuntu Tweak', and backup your desktop settings

sudo add-apt-repository ppa:tualatrix/next

sudo apt-get update

sudo apt-get install ubuntu-tweak [0.6 beta, Oneiric capable]

sudo apt-get install ubuntu-tweak-0 [old version]


```

here is how it looks back the way it was.
[IMG]https://lh6.googleusercontent.com/-vJzZGe_1ZLg/Ulk_J9BVKzI/AAAAAAAAFjA/IKWIWCjq2bA/s1280/Screenshot%2520from%25202013-10-12%252008%253A22%253A15.png[/IMG]

---

### Post by mörgæs on 2013-10-12
Good, then please mark the thread 'solved'.

---

