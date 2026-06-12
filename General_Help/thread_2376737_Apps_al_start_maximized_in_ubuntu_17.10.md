---
title: "Apps al start maximized in ubuntu 17.10"
date: 2017-11-05
forum: General Help
---

### Post by bob brazie on 2017-11-05
Why do all applications start maximized in Ubuntu 17.10?
I would like to stop this behavior but have Goggled it to death and can't find an answer.
Is there a way or can't this seemingly default be changed.
Thanks in advance. Bob.

---

### Post by HNmYk3h on 2017-11-05
This is what I did:

[https://askubuntu.com/a/303119](https://askubuntu.com/a/303119)

---

### Post by bob brazie on 2017-11-06
Which one did you do? 
Are those commands entered into a terminal?
Thanks. Bob.

---

### Post by #&amp;thj^% on 2017-11-06
> **bob brazie said:**
> Which one did you do? 
Are those commands entered into a terminal?
Thanks. Bob.
Just passing by. 
Yes Commands in the Terminal:
```
gsettings set org.gnome.mutter auto-maximize false

```
The code above ^^^ worked for me
You can also set this by dconf-editor.
To reverse:
```
gsettings set org.gnome.mutter auto-maximize true


```

---

### Post by HNmYk3h on 2017-11-06
> **bob brazie said:**
> Which one did you do? 
Are those commands entered into a terminal?
Thanks. Bob.

I used dconf-editor, which can be run either way.  This is a handy tool to have.  Even though I rarely use it, when you need it, it pays for itself ;-)

---

### Post by vasa1 on 2017-11-06
There's a very nice answer over at AU, not on your specific question, but on dconf/gsettings in general: [https://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it/191013#191013](https://askubuntu.com/questions/22313/what-is-dconf-what-is-its-function-and-how-do-i-use-it/191013#191013)

---

