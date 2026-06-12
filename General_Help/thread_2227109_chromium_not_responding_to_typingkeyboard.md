---
title: "chromium not responding to typing/keyboard"
date: 2014-05-30
forum: General Help
---

### Post by Paul_Burden on 2014-05-30
Hi

I'm using kubuntu/ubuntu 14.04 (both have the problem). When using chromium web browser I experience a problem with typing. After a few minutes of use the keyboard input is not picked up by the browser. If I hold a key down then I sometimes get a response after a delay (press a kety and hold for a second or so then several characters will type but the delete key then takes a while to respond). Firefox is fine and other applications respond as expected. Anybody got any idea?

---

### Post by bapoumba on 2014-05-30
Yes, there is a bug : [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
Workaround : ```
ibus exit
```

---

### Post by Dennis N on 2014-05-30
Related: This problem occurs in Lubuntu 14.04 as well.  Specific to Lubuntu there is a permanent fix through Language Support:

```
Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.
```

Permanent, in that once set, you don't need to repeat this. 

Its unclear to me if "ibus exit" needs to be repeated every session. I see in the bug report that "Killing ibus from a terminal with 'ibus exit' is a temporary fix." Any clarification on that?

---

### Post by vasa1 on 2014-05-30
> **Dennis N said:**
> Related: This problem occurs in Lubuntu 14.04 as well.  Specific to Lubuntu there is a permanent fix through Language Support:

```
Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.
```

Permanent, in that once set, you don't need to repeat this. 

Its unclear to me if "ibus exit" needs to be repeated every session. I see in the bug report that "Killing ibus from a terminal with 'ibus exit' is a temporary fix." Any clarification on that?To my mind, **ibus exit** needs to be run after each log in whereas the GUI method described above is permanent in the sense that the changes made there stick even after a reboot.

As soon as I made the GUI change, I looked for which file (in ~/) was modified (or created). IMO, it's ~/.xinputrc. It looks like this:```
# im-config(8) generated on Mon, 26 May 2014 09:59:57 +0530
run_im xim
# im-config signiture: 6edd6bee21c57a8937902546ce39622c  -

```
Yes, it's *signiture* ;)

---

### Post by Dennis N on 2014-05-30
> To my mind, ibus exit needs to be run after each log in whereas the GUI method described above is permanent in the sense that the changes made there stick even after a reboot.


That is what I had thought. What wasn't clear was if 'ibus exit' is equivalent to a kill command (so for the session only) or a persistent toggle switch.

Thanks.

---

### Post by vasa1 on 2014-05-31
@Dennis N, do you have the ~/.xinputrc file? I feel I didn't and that using the GUI you described *created* it. Unfortunately, I don't know how to tell whether a file is created or modified :(

---

### Post by Dennis N on 2014-05-31
> **vasa1 said:**
> @Dennis N, do you have the ~/.xinputrc file? I feel I didn't and that using the GUI you described *created* it. Unfortunately, I don't know how to tell whether a file is created or modified :(

Yes, I have that file, but can't say if it existed prior to changing the setting in the Language Support dialog.

```
dmn@Roxanne:~$ cat .xinputrc
# im-config(8) generated on Sun, 11 May 2014 20:36:14 -0700
run_im xim
# im-config signiture: ab69c350603050fc248bd9f57244bb21  -

```

If you haven't seen it, there is an im-config file in /etc/default

---

### Post by Dennis N on 2014-05-31
Just booted the live session on the installer out of curiosity, and there is no .xinputrc file. It is created when the input method is changed in the Language Support dialog. Confirmed.

---

### Post by vasa1 on 2014-05-31
> **Dennis N said:**
> ...
If you haven't seen it, there is an im-config file in /etc/default
Yes, thanks!

I have that and the only uncommented line in there is this:```
IM_CONFIG_DEFAULT_MODE=auto
```
And that particular file came with the install if its date is anything to go by:```
-rw-r--r--   1 root root   313 Jan  7 19:10 im-config
```

---

### Post by Dennis N on 2014-05-31
Did you see post #8? In there is your answer.

---

### Post by vasa1 on 2014-05-31
> **Dennis N said:**
> Did you see post #8? In there is your answer.

Thanks! I saw it now. All doubts cleared :)

---

### Post by bapoumba on 2014-05-31
Just to add one piece of info.

I have not changed anything to my setup as I want to have it basic to follow how some lubuntu bugs evolve and run some tests if possible. So I'm still using ibus (and temp use Firefox for now, unless I want Chrome for some reason and **ibus exit** at each new session).
```
bapoumba@SonyBlue:~$ cat .xinputrc
# im-config(8) generated on Sun, 27 Apr 2014 13:16:20 +0200
run_im ibus
# im-config signiture: 50608d523caf43cf9d76a497964075dc  -
```

So I guess the file was modified for you both, and not created. April 27th sounds about right for my fresh install over my upgraded lubuntu 14.04.
```

bapoumba@SonyBlue:~$ ls -l /etc/default/im-config
-rw-r--r-- 1 root root 313 janv.  7 14:40 /etc/default/im-config

```

---

### Post by Dennis N on 2014-05-31
> So I guess the file was modified for you both, and not created. April 27th sounds about right for my fresh install over my upgraded lubuntu 14.04.

Good observation. From your evidence, the file .xinputrc is created when installed to HDD. 

So post #8 really only proves it is not present when using the Live USB, and then is created when the Language Support was changed.

If ibus is active, then .xinputrc line #2 should  be **run_im ibus**:

```
lubuntu@lubuntu:~$ cat .xinputrc 
# im-config(8) generated on Sat, 31 May 2014 17:31:04 +0000
run_im ibus
# im-config signiture: 56c4c2e8242f2351069c2773ada22f46  -

```


From LIVE USB test:

Initial contents of home folder:
```
lubuntu@lubuntu:~$ ls -a
.             .bashrc  Desktop    Music     Public     .Xauthority
..            .cache   Documents  Pictures  Templates  .xscreensaver
.bash_logout  .config  Downloads  .profile  Videos     .xsession-errors

```
Change ibus to none:
```
lubuntu@lubuntu:~$ ls -a
.             .cache     Downloads  Public       .xinputrc
..            .config    Music      Templates    .xscreensaver
.bash_logout  Desktop    Pictures   Videos       .xsession-errors
.bashrc       Documents  .profile   .Xauthority

```
contents of .xinputrc after changing ibus to none:
```
lubuntu@lubuntu:~$ cat .xinputrc 
# im-config(8) generated on Sat, 31 May 2014 17:29:32 +0000
run_im xim
# im-config signiture: 5e3081cd9a7ac434f9b733e0d5d7e237  -
```


contents of .xinputrc modified again after changing back to ibus:
```
lubuntu@lubuntu:~$ cat .xinputrc 
# im-config(8) generated on Sat, 31 May 2014 17:31:04 +0000
run_im ibus
# im-config signiture: 56c4c2e8242f2351069c2773ada22f46  -

```

---

### Post by Mike_Hedden on 2014-06-08
I think I might have found the problem with my keyboard...  At first I thought the keyboard had a wire loose but it wasnt loose when I took apart the unit.. I was browsing around on the search engine of Google and something came to mind And I wonder if it was something to do with the Universal Access settings of ubuntu.  This is for those who are having major issues such keyboard is not responding or responding too slow.  Go to All Settings>Universal Access and look for Slow Keys.  There should be a on/off selection option for that; turn it off and your keyboard should respond like it should.

How I discovered this was I was doing a typing test in text editor, well no response well as soon as I held down the key after about 2 seconds later that key responded and started to repeat.  Weird right?  So I wondered if it was the Universal settings and it was.

For those who are having issues with their keyboard not responding, it has nothing to do with the Keyboard Input method, like the Ibus and none option.  I already tried both of those....doesnt work.  This is only for user who have different kinds of keyboards in different languages... Also the on-board keyboard has nothing to do with this as well....

Please spread this discoverey to friends who are having the similar issue.  Obviously this happened after an update

I hope this helps many people who had the same issue as I did for about 2 weeks LOL

PS: Don't waste your time reinstalling, you're still gonna have the same issue 0_e

---

### Post by bapoumba on 2014-06-08
@Mike_Hedden : in my case, only Chromium is affected, no other application, text editors, terminal, Firefox, all of them work as expected.

---

### Post by Mike_Hedden on 2014-06-08
> **bapoumba said:**
> @Mike_Hedden : in my case, only Chromium is affected, no other application, text editors, terminal, Firefox, all of them work as expected.

I couldnt find the topic for people who were having problems with the keyboard like it wouldnt respond at all after login...sorry if its in the wrong topic :P

---

### Post by bapoumba on 2014-06-09
> **Mike_Hedden said:**
> I couldnt find the topic for people who were having problems with the keyboard like it wouldnt respond at all after login...sorry if its in the wrong topic :P
That's OK. If you find it again, we can move your posts over there.

---

### Post by Rob Sayer on 2014-06-14
> **Dennis N said:**
> Related: This problem occurs in Lubuntu 14.04 as well.  Specific to Lubuntu there is a permanent fix through Language Support:

```
Preferences > Language Support > (close any pop up window) > Keyboard Input Method System > change from ibus to none.
```

Permanent, in that once set, you don't need to repeat this. 

Its unclear to me if "ibus exit" needs to be repeated every session. I see in the bug report that "Killing ibus from a terminal with 'ibus exit' is a temporary fix." Any clarification on that?

I just tried this on my Lubuntu 14.04 install, and the keyboard in Chromium worked for a couple of minutes then stopped.

Previously had installed Chrome from their site and it really didn't work so I said sod it and try Chromium instead.

I had Xubuntu 14.04 on for a short period but installed Lubuntu instead.  I don't really like Xubuntu ... it's a bit clunky and nowhere near as fast as LXDE on my 1Gb netbook.

But in Xubuntu 14.04 Chrome worked just fine.  I'm beginning to regret installing Lubuntu again.  Too buggy, not enough fixes.

---

### Post by walterorlin on 2014-06-14
Rob Sayer See post number 3 for a solution to this solution. of using ibus exit as a temporary workaround.

---

### Post by bapoumba on 2014-06-24
Please see here if it helps. Will test it later on.
[https://bugs.launchpad.net/ubuntu/+s...r/+bug/1307648](https://bugs.launchpad.net/ubuntu/+s...r/+bug/1307648)
[https://bugs.launchpad.net/ubuntu/+s...48/comments/21](https://bugs.launchpad.net/ubuntu/+s...48/comments/21)

---

