---
title: "Seek text editor that can autotype specific text"
date: 2021-05-01
forum: General Help
---

### Post by Tom_ZeCat on 2021-05-01
I work as a tech support agent for a software company.  For the longest time I've used a Windows 10 PC with the gVIM text editor to document calls.  I have a file named _vimrc in the VIM program directory that holds all my autotype commands.  For example, if I type "sl", it autotypes "Help creating secondary login".  The code for that autotype is in my _vimrc file as follows: 

```
abbrev sl Help creating secondary login
```

Now I'm going to be able to use my Kubuntu PC for my work, and I'm excited that I can finally get out of Win 10 and all its annoying things.  So, naturally, I would think that gVIM for Linux would be my text app.  So I installed it, and I figured out that its autotext file was in /etc/vim and was named "gvimrc".  It's code is a little different, but it works.  For example, to do the same thing described above, the code is as follows: 

```
:ab sl Help creating secondary login
```

So I coded in all my abbreviations for autotext and now the use of gVIM for Linux should be smooth sailing, right?  Not so fast.  I can't just use the Shift key and an arrow key to highlight text like I can in the Windows version.  I searched around for a command that would let me do that, but haven't found it.  In my Internet searches on the problem, I did find out that I could select text by hitting [esc]+v and then just move the arrows to select it.  However, even after doing that, I can't simply hit Ctrl+C to copy it.  It doesn't copy with that command.  I could of course pull down the Edit menu and choose “copy,” but that's cumbersome.  The purpose of using this text editor is to take notes quickly on whatever the call was about before saving it into the ticket.  Being able to quickly get the text in and then copy it into the ticketing system is of paramount importance.  

I MIGHT be able to get used to hitting [esc]+V and then selecting with the arrows, but I would really miss Ctrl+C to copy the text.  That Alt+E,C would get old.  gVIM/Linux does have a ridiculous copy command which is “+y, that is, the quote key (which requires Shift) and then the plus sign (which is way to the right with the number keys or is the Shift of the equals sign) and then the y key.  I tried it.  It works.  But that's ultra awkward.  

So even though gVIM has worked in Windows, it may not be the best choice for me in Linux.  I've considered some other text editors: 

Notepadqq
This one's interface is exactly what I need, but is there some way I can do my autotext?  It's a HUGE deal being able to just type an abbreviation like “ew” and have it autocomplete “Email address is wrong on the account.”  In gVIM for Windows it saves me a lot of time.  I've looked for in innate command or a plugin for Notepadqq that can do that, but have not found it.

Geany
I love this program!  It's interface is very easy.  If there's some way to do autotext as I'm used to, I would be happy to do my work in Geany.  I've been digging through it's built-in features and have been reading up on plug-ins, but so far haven't found it.  

So there some to be these possibilities: 
1)  gVIM for Linux – How do I make Ctrl+[arrow key] highlight text and Ctrl+C copy text? 
2.  Notepadqq – How do I use abbreviations with autotexting?
3. Geany – Also how do I use abbreviations with autotexting?
4. Some other text program – same as Notepadqq and Geany.  
5. gVIM for Windows run via WINE.  I've tried this.  It does work, but I consider it a last resort, especially when there are so many nice text tools in Linux.

Thank you very much for reading this.  If anyone has any insight on what might work, I would greatly appreciate it.  Thanks.

---

### Post by Holger_Gehrke on 2021-05-02
The word to look for using search engines is 'snippets'.
[Here]("https://www.geany.org/manual/current/index.html#user-definable-snippets") is how to set up autotext and abbreviations in Geany.
Notepadqq doesn't seem to have this feature, but it does have an extension system using JavaScript, so there might be an extension for using and defining snippets out there.

gvim on Linux behaves a lot more like the original vi than it does on Windows. I'm not a fan of vi, but from what little I've read of the documentation it's mostly a matter of finding the right combination of options to set things up the same way it's set up on windows.

The '/etc/vim/gvimrc' is system wide, for user specific options you should use your own ~/.gvimrc ('~' is a short notation for your home directory; the leading dot as part of a file name makes the file 'hidden' so it doesn't clutter up listings in the file manager; all file managers have an option to show hidden files, usually bound to the key ctrl-h).

Holger

---

### Post by HermanAB on 2021-05-02
There are also generic solutions. For example Autotype, which works with anything.

---

### Post by Impavidus on 2021-05-02
I don't use gvim, but I use regular vim in a terminal. I think there are some differences. In particular, everything that gets interpreted by the window manager or the terminal isn't passed on to vim. The user configuration is stored in ~/.vimrc.

You can use esc to get out of editing mode into normal mode, then use v to get to visual mode. Use arrow keys or other movement keys to select a text, then y will copy (yank) it to a register. You don't have to select anything first, as you can also put a movement after the y. y3w in normal mode will yank 3 words. yy will yank the current line, y2j will yank 3 lines. The "x (with x some register name) will select a register for the next yank, delete or paste operation, so you can keep multiple registers. If you're happy using the default register, there's no need to type "+y to copy something. Simple y will do. Note that I can't find anything about the special register + in the vimbook. Maybe specific to gvim?

Have you read the vimbook? It's a 572 page introduction to vim. Use your favourite search engine to find the free pdf. A quick reference sheet may be nice to have too.

---

### Post by Holger_Gehrke on 2021-05-02
He actually does need the '"+' when copying out of gvim to the clipboard for pasting into another program, because '"+' is the register for the clipboard (source: gvim ':help registers', point 8) and yes, that's specific to variants of vim that are written for use in a graphical environment. 

He could try something like 'vmap <C-C>"+y' in ~/.gvimrc to remap strg-c in visual mode to mean 'yank to clipboard', seems to work for me but I haven't really checked for side effects of this (re-)definition . Things like this are the reason the two big old editors (vi and emacs) are still relevant after decades: good documentation and high configurability.

Holger

---

### Post by Tom_ZeCat on 2021-05-02
Thanks for all your help.  I've downloaded the vimbook pdf.  I also continued my searching.  Turns out I needed a couple lines of code to my gvimrc file: 

```
source $VIMRUNTIME/mswin.vim
behave mswin
```
source: [https://superuser.com/questions/10588/how-to-make-cut-copy-paste-in-gvim-on-ubuntu-work-with-ctrlx-ctrlc-ctrlv](https://superuser.com/questions/10588/how-to-make-cut-copy-paste-in-gvim-on-ubuntu-work-with-ctrlx-ctrlc-ctrlv)

It now works exactly as it does on the Windows machine.  I think that other interface must be one that's preferred by some programmers, but I'm not using gVIM for programming.  I'm still going to learn how to use autotype in Geany, as that's an excellent little program that I could use instead of gVIM if I decide to.  Thanks for the link to info on that.

---

### Post by HermanAB on 2021-05-02
This works with anything:
$ sudo apt install autokey

[https://sites.google.com/site/installationubuntu/tools/autokey](https://sites.google.com/site/installationubuntu/tools/autokey)

Note that this utility works with X, so it will work on Xubuntu and Lubuntu, but not with Wayland and Gnome.

---

### Post by Tom_ZeCat on 2021-05-02
> **HermanAB said:**
> This works with anything:
$ sudo apt install autokey

[https://sites.google.com/site/installationubuntu/tools/autokey](https://sites.google.com/site/installationubuntu/tools/autokey)

Note that this utility works with X, so it will work on Xubuntu and Lubuntu, but not with Wayland and Gnome.

That's awesome, man.  I want to thank you, and everyone who helped, with my question.  What I love about the Linux, and the Ubuntu community, is how many knowlegable people there are out there willing to help.  I won't be using Autokey with this particular problem, but I've filed away that info for when it's needed.  I've got both gVIM for Linux and Geany working perfectly with their autotext systems to do what I want.  That means I get to do my day job on my Linux PC, and I don't have to put up with Windows 10 anymore.  While Windows 10 is way, way better than the atrocious Windows operating systems of the past, like Win 95/98/ME, it's still not anywhere near as good as any quality Linux distro like Ubuntu, Kubuntu, Linux Mint, or so many others.  I won't bore you with the annoying things Windows 10 has put me through when I'm trying to do a job, but suffice it to say being able to use a Kubuntu PC instead is liberating.  Windows 10 isn't anywhere near as bad as those awful Windows from the 90s were, but it's still full of major annoyances that Linux users don't have to put up with.

I document and organize everything I install on my two Kubuntu PCs in a CherryTree file.  (CT is an open-source note-taking app that I recommend, btw.)  So I've got your Autokey app documented in there so I can turn to it when I need it.  I've also documented everything I needed to do to get gVIM and Geany doing what I want.  If I ever get back into programming, I may use Geany as my IDE.  I used to program ages ago, but have been out of it for a while.  

Again, many thanks to everyone who helped.  The Ubuntu community is amazing.

---

### Post by dragonfly41 on 2021-05-03
[COLOR=#000000]> CT is an open-source note-taking app that I recommend, btw.

Since you mention CherryTree (a versatile editor which I use extensively) I suggest another option.
Build a toolchain for your workflow using multiple apps, perhaps adding a Python script.

For example Albert has a Snippets extension (and others) and this can be used with CherryTree, Geany and others.

See the Albert Settings and the Python custom extensions.  A "toolchain".

My choice of Albert Hotkey is Num+Enter.
Equivalent in Windows is Listary.[/COLOR]

---

### Post by TheFu on 2021-05-03
If you just want to select and paste text, that's built into X/Windows.
Select any text from any window you like. The selection puts it into the x-buffer.

To paste, click the middle mouse button into any field/file capable of accepting text input.

Bob's your uncle.

vim supports templates or skeleton files.
~/.vimrc:
```
nnoremap ,bash :-1read $HOME/.vim/.skel.bash<CR>
nnoremap ,html :-1read $HOME/.vim/.skel.html<CR>3jwf>a
```
Enter ",bash" into a vim buffer and it will load that template.
The ",html" is a little more featured.

Add as many skeleton files as you like.
Rob's your uncle, this time. ;)

---

