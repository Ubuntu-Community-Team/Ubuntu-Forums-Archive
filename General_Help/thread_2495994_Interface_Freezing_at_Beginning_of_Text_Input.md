---
title: "Interface Freezing at Beginning of Text Input"
date: 2024-03-11
forum: General Help
---

### Post by mark-wootton on 2024-03-11
Hello!   

     
I'm running Ubuntu 22.04.4. A few weeks ago, there was an update  that asked me to restart the computer when it completed. Since then I've  been having a problem with text input.


     Often, if I switch application or text input box within an  application, or go without typing anything for a while, I find that when  I press a key to start typing my computer freezes for a few seconds,  after which it normally writes out the character I was trying to type *twice*,  followed by those I typed before noticing the machine had frozen (e.g.  writing "LLinux" instead of "Linux"). There are a couple of slight  variations on what happens, but it's normally as I just described. As  well as being a nuisance when I try to search or type an address in  Firefox, it also causes a problem when I'm using the terminal a lot for  work -- I'll press the UP arrow key to get my previous command and it'll register twice. Then I'll press enter from muscle-memory and do the wrong thing.


     If I'm typing continuously without pause or switching where I'm  typing (like now for example), I don't have any problems by and large. I  also don't seem to encounter the problem while gaming, as far as I've  noticed.


     I put off asking for help for a while as I hoped that an update  might fix what had been broken by an update, but this has not occurred  some weeks after the fact.   

     Does anyone have any suggestions as how to diagnose and fix this problem? Many thanks to anyone who can help!

---

### Post by dragonfly41 on 2024-03-11
In recent times I experienced problems with my [mouse]("https://www.scottishpoetrylibrary.org.uk/poem/mouse/"). Wired Dell.
I managed to come out of freezing by hitting [Ctrl+Alt+F1] to restart current session.
then I found a reference to Input Remapper app to allow Button Middle (scroll button) to have click [disabled].  It is now tamed.  You might also try a different session LXQT which is first installed then selected at the point of reboot / login / password (look at icon bottom right of screen and select from ubuntu or LXQT). There are other desktop session themes to try.

---

### Post by mark-wootton on 2024-03-11
> I managed to come out of freezing by hitting [Ctrl+Alt+F1] to restart current session.

I should clarify that the freeze only lasts a few seconds before normal behaviour resumes. To give an example, here is a typical sequence of events.

1. I open a new browser window to DDG some term. Let's say "Word".
2. I start typing in the search bar and my interface freezes.
3. A few seconds pass.
4. The interface unfreezes and "WWord" appears in the search bar.

---

### Post by dragonfly41 on 2024-03-11
I went down a lot of blind allies to troubleshoot. I remember Settings > Mouse and  Touchpad > Test Your Settings. And hardware acceleration.  Even today I cannot use Logitech bluetooth keyboard and mouse. But at least I have restored stability with original wired keyboard and mouse. I did not have your exact symptoms but did freeze in browser search bar. I had an escape route [Ctrl+Alt+F1] for a short period.  Try investigating hardware acceleration but this might well be a blind alley.

---

### Post by mark-wootton on 2024-03-11
> I remember Settings > Mouse and  Touchpad > Test Your Settings

I'm only seeing a graphic to show me what my mouse set-up does, which doesn't pertain to my problem.

> [Ctrl+Alt+F1] 

As that's already the default session, it just takes me to the lock screen. If I were to press that key combo during the freeze nothing would happen until the freeze ended, and then I'd have to enter my password again. Even if it responded immediately, it's not a viable work-around given the time wasted repeatedly doing that.

---

### Post by dragonfly41 on 2024-03-11
This is a guessing game. Reflecting on the clues (gaming, fast typing) this discussion seems to fit the profile.

[https://ubuntuforums.org/archive/index.php/t-1330013.html](https://ubuntuforums.org/archive/index.php/t-1330013.html)

---

### Post by dragonfly41 on 2024-03-11
I mentioned Input Remapper in post #2. As I guessed it *might* be used to introduce key delays to stop stuttering at beginning of capitalised words..

[https://www.linuxuprising.com/2020/12/remap-keyboard-and-mouse-buttons-on.html](https://www.linuxuprising.com/2020/12/remap-keyboard-and-mouse-buttons-on.html)

---

### Post by mark-wootton on 2024-03-12
That's a different problem to the one I'm having I'm afraid. When the problem manifests, it occurs even if I press only a single key. It's also not contingent on me typing an uppercase letter or any letter at all -- e.g. pressing the UP-key in the terminal to get my last command or pressing control-V in a text editor. I don't think setting up a keyboard macro is going to help me. It seems clear that something is going wrong at a software level insofar as my OS should not be freezing for a few seconds just because I started typing in a new window/text box in a window and indeed, until that update a few weeks ago, everything worked perfectly fine.

---

### Post by dragonfly41 on 2024-03-12
(a) Same symptoms experienced in LiveUSB "Try Ubuntu" mode?
(b) Same symptoms experienced in say X or Wayland or LXQT sessions?
(c) "[COLOR=#000000] it occurs even if I press only a single key" sounds like "sticky key" syndrome.
(d) Try tests such as this .. [/COLOR]https://joltfly.com/keyboard-scan-rate-test/
[COLOR=#000000]Guessing game continues ...

PostScript: You did write in an earlier post "[/COLOR][COLOR=#000000]The interface unfreezes and "WWord" appears in the search bar.". I interpreted from this that your symptoms were at start of sentence. And prossbly linked to your "muscle memory" you mentioned.

That is after typing:  [.][space][W].

But now you explain "any key".

Hence the wild goose chase.[/COLOR]

---

### Post by mark-wootton on 2024-03-12
Firstly, thank you for your time so far in helping me.

> [COLOR=#000000]PostScript: You did write in an earlier post "[/COLOR][COLOR=#000000]The  interface unfreezes and "WWord" appears in the search bar.". I  interpreted from this that your symptoms were at start of sentence. And  prossbly linked to your "muscle memory" you mentioned. [/COLOR][COLOR=#000000]That is after typing:  [.][space][W].[/COLOR]
[COLOR=#000000]
I think I see now where I have been unclear. The problem typically manifests at the first keystroke following switching window or switching between text entry boxes within a window (not every time, mind you) -- so there is no instance of [/COLOR][COLOR=#000000]"[.][space][W]" as in that example, I was trying to communicate that the first key pressed was "W" itself. While the interface is frozen, it does seem that keys pressed in that duration are (mostly) registered, so if I've pressed a few keys, they normally appear at the same time, typically in the correct order (So "WWord" or very occasionally "WoWrd" appears as the computer unfrezes). However, if I press more than one or two words' worth of keys, it is likely that some will be loss when the computer unfreezes.

My reference to muscle memory pertained to the particular way this problem inconveniences me while working in a terminal, that is, I switch to a terminal window with the intent of repeating my last action, I press UP to see my last command and then ENTER the execute, but instead run the command prior to that because the computer froze when I pressed UP and then acted as if I'd pressed it twice. I should probably try to unlearn my habit of pressing UP and ENTER in quick succession, but I'd rather my computer didn't freeze in the first place too.
[/COLOR]
As to the proposed diagnostics:

* I will try a. and/or b. later, see where I get to, and report back
* I don't think I have a physical problem with my keyboard, if that's what you mean. The problem started exactly after I ran an update and rebooted a few weeks ago, it seems to effect every key in exactly the same fashion, and it seems to have a very precise, if intermittent, trigger.
* I will attempt to trigger the problem while interacting with that site, but so far have not been able to do so.

---

### Post by dragonfly41 on 2024-03-12
There is one tool I am using right now (as I write) for an entirely different purpose to automate interaction with a tool chain of multiple applications. That is emulating user interface. This venerable tool is Actiona in the repo.

sudo apt install actiona

Now if you launch the GUI ..simple launch actiona through [Alt+F2] .. you can use this to monitor interactions with keyboard and dump to console various data.

Thus to start you off drag "Key Condition" widget to central panel .

In the Key Condition widget you can look for a particular key or multiple keys and execute an action or Call Procedure.

You will need the Loop widget to keep monitoring the Key Condition.

This might give insights into what is occurring when defined "Key Conditions" are met. Observing key operations.

You will also need Console widget to log events.

I recommend bulding Procedures to call.

I write my code in external Sublime Text editor since the Actiona internal code editor uses tiny fonts.

This may not answer your question about why you have this change but it will give more insights into what is going on. Note that you can also call Command widget.

---

### Post by dragonfly41 on 2024-03-12
Another tip:

The description of your case I researched as "key stuttering" and this opens up a further can of worms.

[https://askubuntu.com/questions/1404531/ubuntu-22-04-stuttering](https://askubuntu.com/questions/1404531/ubuntu-22-04-stuttering)

Some users have reported stuttering issues on Ubuntu 22.04 with Wayland. Try switching to Xorg if you're currently using Wayland, as this could potentially resolve the issue. You can do this by logging out, clicking the gear icon on the login screen, and selecting an Xorg session before logging back in.  I did suggest earlier that you try different sessions (switch out of Wayland) . 

[https://askubuntu.com/questions/1410256/how-do-i-use-x-instead-of-wayland-on-22-04](https://askubuntu.com/questions/1410256/how-do-i-use-x-instead-of-wayland-on-22-04)

But nevertheless as a separate line of attack Actiona can still be used to monitor UP and ENTER (or other) keys.

---

### Post by mark-wootton on 2024-03-13
> Actiona

I will take a look at that. Thank you.

I was  using X.Org, but following your suggestion, I've switch to Wayland. In  the ~24 hours since, I have had no instances of my reported problem.

That said,  I've had a slightly different problem under Wayland -- if I haven't  interacted with my computer for a while, I sometimes get a one or two  seconds of freeze/stuttering after I move the mouse again, and I've also  seen a couple of instances of a similar effect when I open the  workspace overview. However, this is a much better situation than the  issue with text input, so this is certainly a step up. Even if I don't  get any further, I can tolerate this at least.

I might also add,  that I have the seconds shown on my top-bar clock, which is why I know  that it's the interface itself freezing. I previously forgot that this  isn't part of the default display.

-----

Edit: Ps, I have an AMD graphics card.

---

### Post by dragonfly41 on 2024-03-13
This link which I found for a different reason explains how to install tasksel and switch between desktop sessions. Might be a useful experiment to try different modes.

[https://www.reddit.com/r/linux4noobs/comments/1433t47/how_to_install_another_desktop_environment_in/](https://www.reddit.com/r/linux4noobs/comments/1433t47/how_to_install_another_desktop_environment_in/)

I continue my own usage of Actiona for desktop orchestration.

P.S. also xdotool must be mentioned.

---

### Post by mark-wootton on 2024-03-23
Just an update on this: I've been using Wayland instead of X11 since my  last post, and have had a close to perfect experience, just very  occasional stuttering when I open the workspace overview or move the  mouse for the first time in a while. I'm telling you this because I  don't want to disrespect the time you've spent advising me thus far. I  do intend to go back to X11 and try the various tools you suggest, but  I've been too busy recently to justify doing so, so it'll have to wait  until I have more free time.

---

### Post by dragonfly41 on 2024-03-23
Apparently Actiona (which interacts with user interface) does not work in Wayland (or so I read).
Something to do with Wayland security policy since it can be risky if rogue scripts slip through. But I intend to stay with X11. Actiona is a key tool in my toolkit allowing interactions between applications and GUI's.  Regarding time for experiments I am just returning to a post I penned elsewhere some three years ago. Tempus fugit.

---

