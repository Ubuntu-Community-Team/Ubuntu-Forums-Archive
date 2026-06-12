---
title: "Can't type character &quot;P&quot; uppercase in terminal: it just won't accept it"
date: 2015-02-10
forum: General Help
---

### Post by leon.lain.delysid on 2015-02-10
Hello fellow GNU lovers!

I guess I can safely say I found a very weird bug, of which I haven't found any single reference anywhere on the Internet. So I have got to post here to ask for suggestions and general help with my issue.
The issue:
I can't type the letter P in its uppercase form in my terminal... When I try entering one on my keyboard, it's just as if nothing happens.
[LIST]
[*]Shift+P won't type an uppercase P in the terminal, does nothing instead. 
[*]Copy "P" and paste into terminal will result in nothing pasted. 
[*]Copy "Pokemon" and paste into terminal will result in "okemon". 
[*]Typing an uppercase 'P' or copy-pasting it in any other program will work as expected (like here in Firefox, or there in gedit). 
[/LIST]
I can, however, autocomplete a folder name from "pokemon" to "Pokemon". Or have an access to a "SPACE" folder by just typing "sp" and then autocomplete using TAB. (For curious people who don't know how to be able to have autocomplete ignore case this way, you have to activate it in a [FONT=courier new]~/.inputrc[/FONT] file by pasting in this file the command [FONT=courier new]set completion-ignore-case on[/FONT].)
However, it just got annoying a few moments ago when I wanted to [FONT=courier new]rsync Pokemon /my_new_folder/[/FONT] because then the autocomplete doesn't work (I don't know why, maybe rsync doesn't have it).

So, putting aside the issue of being able to copy this specific folder, which there are millions of other ways of doing it (and I'm going to pick one and just do it right after I posted this), I'd like to be able to type uppercase 'P' characters again into my terminal... ^^''
So does anyone have a clue what I could do? Why this is happening to my terminal? What tests I could run to figure out how this is possible?

Thank you for reading! Thanks for caring! =)

PS: By the way, I'm on Ubuntu Gnome 14.10. I think I had this problem before, that it's not new. And, checking my laptop with Ubuntu 13.10... the terminal does accept the uppercase 'P' character as expected, no problem there.

---

### Post by kpatz on 2015-02-10
How about someplace other than the terminal, such as Gedit or some other text editor, web browser, email client, etc.?  Does uppercase P work in those places?

If not, it could be a faulty keyboard.  What happens if you hold down the Alt key and type "80" on the numeric keypad?  Do you get an uppercase P then?

Desktop or laptop?  Try toggling NumLock or FnLock if it exists.

---

### Post by leon.lain.delysid on 2015-02-10
I only have this problem in the terminal. Gedit or Firefox or any other program will work fine. p P ^ ¨ O o M m P
Alt+80 won't do anything, be it in terminal or gedit.
This computer is a desktop. I have no FnLock. Toggling NumLock changes nothing to the problem.
I also tried CapsLock instead of using Shift, but still no uppercase 'P' in my terminal.
By the way also, my keyboard layout is "French (alternative)" (I have an azerty keyboard).

---

### Post by kpatz on 2015-02-10
Can you try another keyboard layout?  There are probably other azerty options.

I just installed 14.10 in a VM using French azerty and capital P works for me.  But I have a regular US keyboard so I can't type a lot of other letters!

Just tried French alternative (didn't see French alternative azerty on the list) and P works there as well.

---

### Post by Impavidus on 2015-02-10
Can you type a P in a different terminal? Try for example in xterm instead of the default terminal, or on the console. That may tell us whether it's a terminal config problem. And can you type P when you use a guest session?

BTW, typing alt+<decimal code> is the Windows way of entering special characters. On Ubuntu you use ctrl+shift+u, <hexadecimal code>.

---

### Post by leon.lain.delysid on 2015-02-10
OK, so I tried with the "English (US)" layout, and I still can't type in 'P'.

Now, I tried going over to the console in Ctrl+Alt+F1, and I could type a 'P' in the login name, but not inside my logged in session.
So I tried another user, and on that user session, I can type the 'P'.
So it's definitely something that's got to do with my own user.
I added stuff to [FONT=courier new].bashrc[/FONT], so I'm going to try and withdraw whatever I added one by one, and see. I'll inform here later.

---

### Post by leon.lain.delysid on 2015-02-10
Alright! I found the answer! ;)

Here's what I did:
I wanted to personalize my bash visually. So I created my own personalization :
```
PS1="\[\e]0;\u@\h: \w\a\]\[\033[00;35m\][\t] \[\033[00;32m\]$(if [[ 1000 == 0 ]]; then echo '\[\033[01;31m\]'; else echo '\[\033[00;32m\]'; fi)\u@\h\[\033[00;30m\]:\[\033[01;34m\]\w\n$(if [[ 1000 == 0 ]]; then echo '\[\033[01;31m\]#'; else echo '\[\033[01;34m\]\$'; fi) \[\033[00m\]";
```
And then I put it inside [FONT=courier new].bashrc[/FONT]. But then I also put it in [FONT=courier new].inputrc[/FONT], because I thought that made more sense. So it was in both files. (I don't know why I didn't take it out of [FONT=courier new].bashrc[/FONT]. Surely because then the personalization wouldn't work at all. So I put it back into [FONT=courier new].bashrc[/FONT], forgetting to take it out of [FONT=courier new].inputrc[/FONT].)
So now taking it out of [FONT=courier new].inputrc[/FONT] solved my problem.
Now if one of you can tell me how "obviously I couldn't put it there because of this and that reason", I'd be curious to ask and grateful to be told. =) To me, It should belong in [FONT=courier new].inputrc[/FONT], shouldn't it? Well, [FONT=courier new].bashrc[/FONT] isn't a bad place to put it in also I guess.

---

### Post by Holger_Gehrke on 2015-02-10
Could it be that you tried to redefine some readline key bindings in the ~/inputrc and made a typo ?

**Edit:** I see you found it. Well, that's what I get for not refreshing after looking in the manual and before posting ...

> 
Now if one of you can tell me how "obviously I couldn't put it there  because of this and that reason", I'd be curious to ask and grateful to  be told. =) To me, It should belong in [FONT=courier new].inputrc[/FONT], shouldn't it? Well, [FONT=courier new].bashrc[/FONT] isn't a bad place to put it in also I guess.


And of course defining your prompt in inputrc makes no sense whatever because ~/.inputrc is the configuration for the readline library which is used by all kinds of programs (mostly interactive interpreters like python or perl but also the mysql command line client)  that need line editing and all the other things readline provides.

---

### Post by Impavidus on 2015-02-11
If this has been solved, could you mark the thread as solved? Thread tools (near top of page) -> mark as solved.

---

### Post by leon.lain.delysid on 2015-02-11
Yes, thank you all for your help!
I'm happy I can type uppercase 'P's again. =)

(And thanks for the "SOLVED" tip, it's very practical.)

---

