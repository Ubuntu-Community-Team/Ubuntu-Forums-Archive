---
title: "Using Find in Gnome terminal"
date: 2008-05-30
forum: General Help
---

### Post by kung_fu_mike on 2008-05-30
Please understand that this may be vague as I am asking the question from the perspective of a 3rd party. The essential question is this:

In gnome terminal I have just run a command. There are approximately 500 lines in the screen buffer. How do I search those lines without running the command over again?

here is the chat context in case it helps:

(01:35:43 PM) Nojan: hi, question for you
(01:35:52 PM) mike: shoot
(01:35:59 PM) Nojan: you use ubuntu .....
(01:36:04 PM) mike: exclusively
(01:36:05 PM) Nojan: what terminal do you use
(01:36:17 PM) Nojan: i just realized the gnome terminal has no FIND??
(01:36:23 PM) Nojan: wtf
(01:36:43 PM) mike: really
(01:37:08 PM) Nojan: i can't find it
(01:37:13 PM) Nojan: or it doesn't exist
(01:37:15 PM) mike: huh
(01:37:23 PM) mike: I have to admit I never noticed
(01:37:25 PM) Nojan: isn't that crazy?
(01:37:29 PM) mike: I use locate more then anything
(01:37:32 PM) mike: yeah it is
(01:37:46 PM) mike: I use the gnome terminal with bash
(01:37:50 PM) Nojan: let's say you "cat"  or "less" 200 lines of text and want to find something quickly
(01:37:53 PM) mike: or gnome terminal with rush
(01:38:10 PM) mike: I guess I just use grep
(01:38:16 PM) mike: but yeah you are right
(01:38:26 PM) Nojan: yeah, grep sure
(01:38:30 PM) Nojan: but it's an extra step
(01:38:35 PM) Nojan: redirect output to a file.... then search
(01:39:04 PM) Nojan: 'cuz it's kind of a pain to get grep to give you 5 or 6 lines on either side of the match
(01:39:17 PM) mike: yeah
(01:39:21 PM) mike: no I totally follow you
(01:39:32 PM) mike: you can always convert...
(01:39:33 PM) mike: {link to rush here}
(01:39:51 PM) mike: that will give you your find
(01:39:51 PM) Nojan: what is it, rush?
(01:39:55 PM) mike: yup
(01:40:02 PM) mike: its a pure ruby commandline
(01:40:09 PM) Nojan: but that's a shell
(01:40:19 PM) Nojan: i'm talking one level above that
(01:40:20 PM) mike: its functionally both
(01:40:27 PM) mike: yeah
(01:40:32 PM) mike: yeah I guess you are right
(01:40:35 PM) Nojan: rush looks nice
(01:40:41 PM) Nojan: but ..
(01:40:45 PM) mike: I was just looking for work arounds or solutions
(01:41:03 PM) mike: of course the point is I shouldn't have to
(01:41:08 PM) mike: I don't know what to tell you
(01:42:12 PM) Nojan: no, that's cool
(01:42:16 PM) Nojan: just wanted a sanity check
(01:42:21 PM) Nojan: i'm so spoiled by apple
(01:42:24 PM) mike: I am not getting anything about it from google either
(01:43:47 PM) mike: wait
(01:43:49 PM) mike: ok
(01:44:09 PM) mike: so in your terminal you can't type find /log syslog
(01:44:22 PM) Nojan: no, that's not what i'm talking about
(01:44:33 PM) Nojan: let's say i have 500 lines of stuff in the terminal buffer
(01:44:39 PM) Nojan: it's on the screen already
(01:44:43 PM) mike: ok
(01:45:08 PM) Nojan: and i want to jump to the line that contains  10.10.10.10 
(01:45:12 PM) Nojan: or whatever arbitary string
(01:45:21 PM) Nojan: just like you would in a browser or any other app
(01:45:37 PM) mike: humm
(01:45:40 PM) mike: damnit
(01:46:24 PM) mike: I am looking for a means to enter copy mode
(01:46:32 PM) mike: I am assuming you are using vi as you bash editor
(01:47:12 PM) Nojan: i use tcsh, but that's irrelevant
(01:47:23 PM) mike: only slightly
(01:47:33 PM) mike: I was considering a workaround I use in screen sessions
(01:47:42 PM) Nojan: oh yeah
(01:47:44 PM) mike: in screen you can ctrl-A esc
(01:47:45 PM) Nojan: nahh, don't worry
(01:47:58 PM) mike: go into copy mode and use standard / search functionality
(01:48:00 PM) Nojan: i was just hoping i was missing something basic
(01:48:06 PM) mike: not that I know of
(01:48:22 PM) mike: but remember I am not really a sys/admin style linux pro
(01:48:31 PM) mike: I am more of a programmer
(01:49:12 PM) Nojan: yeah, but you're smart :) 
(01:49:20 PM) Nojan: i'm just annoyed, been spoiled by the mac
(01:49:33 PM) mike: well thank god cause I didn't come out pretty
(01:49:33 PM) Nojan: i keep running into things i wish ubuntu did , that the mac does
(01:49:36 PM) Nojan: hehehehe

---

### Post by Koybe on 2008-05-30
I haven't read the whole conversation but usual way is :
```
your_command | grep your_search
ex: cat /var/log/syslog | grep failed
```

You can also use -i with grep if you don't want to be case sensitive.

---

### Post by kung_fu_mike on 2008-05-30
actually one of the primary goals was to not run the command again. Thus grep is not really the best solution.

---

### Post by VMC on 2008-05-30
I'm not quite sure I understand the question, but if you are keeping the terminal open just to find something you could do a cut & paste to a file. Then open the file and use the search function or cat the file and pipe the output.. or just run the command again and append the with a pipe, like so: 'find / -name *.c -print|grep lex'.

---

### Post by Koybe on 2008-05-30
I don't get it. What's the problem hiting upper key and add grep to your line? Maybe some terminal other then gnome terminal should do this. Just have a look and try.

---

### Post by kung_fu_mike on 2008-05-30
The problem may be that the output is unique, or performs a dangerous action I don't want to risk repeating. An easy example would be a compiler dump. Here I am with 500 lines of errors on my screen. I have that data, it exists somewhere. I would like to search it without trying to compile again. It would be nice to just type find 'foo', or find_in_buffer. I am really hoping someone knows how to access the screen buffer and we can dump that into grep in one quick action.

---

