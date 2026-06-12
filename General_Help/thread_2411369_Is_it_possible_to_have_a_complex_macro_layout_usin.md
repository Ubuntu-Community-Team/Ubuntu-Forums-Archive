---
title: "Is it possible to have a complex macro layout using multiple keyboards?"
date: 2019-01-29
forum: General Help
---

### Post by abdoo-892005 on 2019-01-29
I am a video editor and I love to rely mostly on the keyboard. The  software I use allows me to create loads of shortcuts for all the  commands I like to use. However, for some of these commands, I might  have to use a combination that includes **CTRL+SHIFT+ALT+SOME KEY**, which slows down the process for me a little bit.

  
What I would like to do is get another keyboard, where I can use one  as the main input keyboard, and use the other one as a macro keyboard  where I can assign some of the keys to those complex shortcuts.

  The macro keyboards I have managed to find all seem to rely on some  software that doesn't have a Linux version (correct me if I am wrong).

  
So I wanted to see if there is a way where I can replicate the  functionality of those macro keyboards on Linux. I will try clarifying  in detail what I would like to do.


  
[LIST=1]
[*]I have two keyboards. 
[*]First one used regularly as an input device for typing or any normal input. 
[*]Second one is used to simulate specific key strokes and combinations. 
[*]This way, if I click the **S** key for instance on the first keyboard, it sends an s keystroke, but if I press it on the second keyboard, it sends what key combination I have defined, let's say **CTRL+SHIFT+ALT+Y**, for instance. 
[/LIST]
  
I have looked online and some posts suggested *AutoKey *or *xdotool*.  Aside from the fact that I couldn't get any of them to work properly, I  also don't see a way to define which specific keyboard I would like to  use.

  I am using Ubuntu 18.04 MATE.

---

### Post by vanadium on 2019-01-29
Maybe this can help you: [Askubuntu](https://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04/347382#347382?newreg=4eb097870a15490ebbe39d78412f9797)
which refers to the [Community documentation](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions).

---

### Post by abdoo-892005 on 2019-01-29
XKB looks like an option, but I am trying to wrap my head around it.. One thing that is annoying me about it though is the fact that I use multiple layouts on my machine already for typing.. When I set a different layout to one of the keyboards, the other layouts disappear from the tray icon.

---

### Post by dragonfly41 on 2019-01-29
There is an application Actiona which you might find under accessories. If not it is in Software Centre.
You can use the GUI to create a script which simulates key strokes including Ctrl Alt Shift Meta and other keys.
Save the script as say mykeys.ascr then you can run the script using command ```
actexec mykeys.ascr
```.

---

### Post by abdoo-892005 on 2019-01-29
> **dragonfly41 said:**
> There is an application Actiona which you might find under accessories. If not it is in Software Centre.
You can use the GUI to create a script which simulates key strokes including Ctrl Alt Shift Meta and other keys.
Save the script as say mykeys.ascr then you can run the script using command ```
actexec mykeys.ascr
```.
That's really an amazing piece of software. One thing, though, how can I then make only one of the two keyboards executes the script using the shortcut.

On Ask Ubuntu, `actkbd` was recommended for that. I tried it with both `xdotool` and `Actiona` and it works in both cases. The only problem, though, is that it hasn't seen any development in years. I would rather use something that is still maintained or native to Linux in case I need some help.

Here is the link for the same question on Ask Ubuntu: [https://askubuntu.com/questions/1113803/is-it-possible-to-have-a-complex-macro-layout-using-multiple-keyboards](https://askubuntu.com/questions/1113803/is-it-possible-to-have-a-complex-macro-layout-using-multiple-keyboards)

---

### Post by dragonfly41 on 2019-01-29
I have no experience in using two keyboards or actkbd. I did find [this thread]("https://unix.stackexchange.com/questions/35649/second-keyboard-to-run-commands") which might give you some tips.
In fact if you use Actiona scripts do you need a second keyboard?
Just another point .. under Applications > Universal Access I can launch virtual keyboards on screen. 
Florence and Onboard.  Would these be useful?

P.S. I see that the thread I found is in fact referenced earlier above.
On further thought I would just use Actiona to *respond* to one key set which in fact *emulates* hitting another key set.

And as another thought you can write python scripts to respond to key presses .. [see here]("http://www.jonwitts.co.uk/archives/896") .. and
another python script to emulate key presses .. [see here]("https://nitratine.net/blog/post/simulate-keypresses-in-python/")

---

### Post by abdoo-892005 on 2019-01-30
> **dragonfly41 said:**
> I have no experience in using two keyboards or actkbd. I did find [this thread]("https://unix.stackexchange.com/questions/35649/second-keyboard-to-run-commands") which might give you some tips.
In fact if you use Actiona scripts do you need a second keyboard?
Just another point .. under Applications > Universal Access I can launch virtual keyboards on screen. 
Florence and Onboard.  Would these be useful?

P.S. I see that the thread I found is in fact referenced earlier above.
On further thought I would just use Actiona to *respond* to one key set which in fact *emulates* hitting another key set.

And as another thought you can write python scripts to respond to key presses .. [see here]("http://www.jonwitts.co.uk/archives/896") .. and
another python script to emulate key presses .. [see here]("https://nitratine.net/blog/post/simulate-keypresses-in-python/")
The whole reason I need this is the fact that, with one keyboard, shortcuts tend to get very complicated very quickly, especially when using a video editing software. If I only rely on the Actiona scripts and call them using shortcuts, that won't solve the issue. In fact, it might even complicate it, because I will have to avoid the shortcuts that are already used in the program, as well as any OS-level shortcuts.

And virtual keyboards won't solve the problem as well... I personally prefer to rely on the keyboard rather than the mouse, especially when editing. The less I use the mouse, the faster I am.

For now, I will keep using **actkbd**. It is working really well. It is just I am worried that, since it is no longer maintained, any future updates to the OS might break it. Looks like I will have to cross that bridge when I get to it.

Thank you for your help, guys. I really appreciate it.

---

