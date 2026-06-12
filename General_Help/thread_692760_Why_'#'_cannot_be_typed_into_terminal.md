---
title: "Why '#' cannot be typed into terminal?"
date: 2008-02-10
forum: General Help
---

### Post by Ahxun on 2008-02-10
Im using Ubuntu terminal. After i have created a new file want to build my c programming.

The heading i wan to type #<include>...

Problem is.. i cannot type '#' into terminal.

What is the problem? Is it i need to install anything to upgrade it?

Please teach me how to do it.. Thank you!

---

### Post by danwood76 on 2008-02-10
you should be able to type the # in terminal.
Do you have your keyboard layout setup correctly?

---

### Post by Ahxun on 2008-02-10
I can type # normally..

But after i use vi create a new file enter the text editor. I cannot type # as first word or heading.

It show me this red message at the bottom:

"E348: No string under cursor"

So what can i do to solve this problem? Please help me...

---

### Post by danwood76 on 2008-02-10
you could try using nano instead of vi.
I will probably get flamed for saying this but nano is easier to use and better in my opinion.

its more like a standard text editor.

---

### Post by Ahxun on 2008-02-10
About my problem, my friend used to solved it by download n upgrade somethings in Ubuntu.

But he forgot the steps already. Can you help me?

I have to use vi text editor to complete my job, anyway thanks to your suggestions.

---

### Post by sujoy on 2008-02-10
remember this: 
vi has two modes
1. text mode
2. command mode

when you type in at the terminal

**vi filename**

vi starts in command mode. 

just press **i** once, it will change vi into insert mode. now type anything and when you are finished, press the **escape** key (goes back to command mode), then type

**:w** (this will save the file)
**:q **(this will quit)

or you can do 
**:wq** (to save and then exit)

or else 
**:q! **(to quit without saving)


remember: you start vi, press **i** to go into insert modem, type press **escape** key and then do **:w** , **:q**, **:wq** or **:q!**

---

### Post by spec-chum on 2008-02-10
That's definitely an error from the vi editor, not the terminal.

To enter text in the vi editor you need to press i to enter insert mode.  If you try to enter a # sign without first entering insert mode you'll get that error.

As previously suggested you may find nano easier to get started with.  vi is a fantastic editor but it takes some work to get used to.

---

### Post by Ahxun on 2008-02-10
I see...

I have tried to type i, but it didn't make into insert mode.

It only has recording mode.

So i wonder is it my text editor less some function?

---

### Post by meindian523 on 2008-02-10
or you might need to use 'a' for insert mode.Vi in Ubuntu points to Vim which automatically recognizes that you are typing text and allows you to continue.If you went back and typed #,it would be possible.I'm always forgetting which is the letter for insert mode,but it's either 'i' or 'a'.So try 'a' now.

---

### Post by spec-chum on 2008-02-10
> **Ahxun said:**
> I see...

I have tried to type i, but it didn't make into insert mode.

It only has recording mode.

So i wonder is it my text editor less some function?

It shouldn't be.  This is in every version of vi ever.

You shouldn't be getting into recording mode by pressing 'i'.

You are just doing something like the following yes?

```

$ vi myprogram.c

```

Then when in vi just press the i key.  When you do this you should see the line
```

-- INSERT --

```
 
at the bottom left of the window.  You can then start typing your program, probably something like

```

#include <stdio.h>

int main()
{
        printf("Hello World!\n");
        return 0;
}
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
-- INSERT --                                                  7,2           All

```

if you then press Escape you'll leave insert mode and can then type :wq to write the changes away and quit.

---

### Post by Ahxun on 2008-02-10
I have tried your steps already. The insert mode is not showed after i press 'i'.

But just now i get insert mode in vim editor and success to type '#'.

What is the different between vi n vim? Is it vim can use for programming like c or c++?

I tried to compiled but failed, it said there is no stdio.h file or directory.

Is it i have to download the eclipse to upgrade it?

---

### Post by spec-chum on 2008-02-10
It sounds like there was an issue with your vi.  Weird.

Anyhow, to compile C programs on your system you'll need the build-essential package installed.
Either run Synaptic and search for build-essential and install it from there or enter
```

sudo apt-get install build-essential

```
in the terminal.

After you've installed that the compiler should be able to find stdio.h.

---

### Post by seventhc on 2008-02-10
open a terminal and try this
```

vimtutor
```

hmm, the '*i'* should work in both *vi* and [I]vim.
vim [/I]is supposed to be[I] vi improved
[/I]

---

### Post by Ahxun on 2008-02-10
I have typed in the code into terminal to install, but it showed me this message:

"Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter"

I have inserted the Ubuntu CD, but after i pressed enter there is nothing to show out.

What should i do in next step? Please teach me..

---

### Post by seventhc on 2008-02-10
Go to *System>Administration>Software Sources* and uncheck the cd option.
then try it again

---

### Post by meindian523 on 2008-02-11
and make sure your online repositories are enabled,mainly the main and universe.

---

