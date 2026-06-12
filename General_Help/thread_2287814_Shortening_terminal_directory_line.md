---
title: "Shortening terminal directory line"
date: 2015-07-22
forum: General Help
---

### Post by terry36 on 2015-07-22
Hello all, 

I have been using Ubuntu for a couple of years and I have learned to absolutely love this linux distro. The only issue I am having, or annoyance, really, is that I spend a lot of time in the terminal and when I get deep into a sub directory, it takes up pretty much the entire line. I understand this is something that happens no matter what shell or OS you use. 

For example, What I have: [HTML]me@me:~/workspace/codingProject/subdir/subdir/subdir$[/HTML]

and what I want: [HTML]me@me:~$[/HTML]
I would like it to display that all the time, and then I could 
[HTML]pwd 
home/me/workspace/codingProject/subdir/subdir/subdir [/HTML]

If I ever wanted to find out exactly where I was. Is there any elegant tool that does this, or is this baked into the core system? I am coming here because I couldn't even begin to think of how to phrase this to put into google. 

not sure if it's relevant, but I am running 64bit Ubuntu 14.04.2 LTS trusty

Thank you for the help!

---

### Post by howefield on 2015-07-22
Try appending something to the end of your ~/.bashrc file eg,

```
export PS1='me@me:~$ '
```

---

### Post by terry36 on 2015-07-22
That did the trick! Thank you so much!!

---

### Post by howefield on 2015-07-22
Welcome :)

---

### Post by vasa1 on 2015-07-22
> **howefield said:**
> Try appending something to the end of your ~/.bashrc file eg,

```
**export** PS1='me@me:~$ '
```

Is "export" necessary? I get the same prompt even if I leave out "export".

---

### Post by Lars Noodén on 2015-07-22
The default for $PS1 inlcudes \w which shows the full path.  If you do \W with an uppercase W then it displays only the basename.  The full list of back-slash-escaped special characters can be found in the [bash](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html) manual page under the section for "prompting"

```

PS1="\W \$ "

```

---

### Post by steeldriver on 2015-07-22
Another option is to use the PROMPT_DIRTRIM variable

```

PROMPT_DIRTRIM
              If  set  to a number greater than zero, the value is used as the
              number of trailing directory components to retain when expanding
              the  \w  and  \W  prompt  string  escapes (see PROMPTING below).
              Characters removed are replaced with an ellipsis.

```

e.g.

```

steeldriver@T61p:~/Documents/forums/subdir/subdir/subdir/subdir/subdir/subdir$ PROMPT_DIRTRIM=3
steeldriver@T61p:~/.../subdir/subdir/subdir$

```

---

### Post by terry36 on 2015-07-22
> **Lars Noodén said:**
> The default for $PS1 inlcudes \w which shows the full path. If you do \W with an uppercase W then it displays only the basename. The full list of back-slash-escaped special characters can be found in the [bash]("http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html") manual page under the section for "prompting"

```

PS1="\W \$ "

```


Ohhhhhh, that is really slick. Thank you for that. This method is actually even better than what I had in mind. And thank you for the reference, I will be bookmarking that.

---

### Post by vasa1 on 2015-07-23
Good question and great answers!

I've added ```
PROMPT_DIRTRIM=2
```to the end of my *.bashrc*.

---

