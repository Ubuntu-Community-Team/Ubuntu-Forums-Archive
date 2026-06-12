---
title: "Copy and paste within terminal"
date: 2007-03-30
forum: General Help
---

### Post by zorkerz on 2007-03-30
I have been trying to find a way to copy and past without using the mouse from within the a terminal.  sometimes when typing a command i know i will need part of the text again and again i would like to know if it is possible to first highlight it and then copy it without a mouse.

---

### Post by acormack on 2007-03-30
zorkerz

This is an intersting question and I dont have a proper answer.

you might be able to use the history command (man history) to get access to the command which you could save in a file or shell variable.

Also just typing !! gives the last command.

Can you give more details of what you are tryng to achieve?

Alec

---

### Post by zorkerz on 2007-03-30
also pressing the up arrow for me cycles through previous commands.

When i am writing a paper or even right here i can press shift and use the arrow keys to highlight text and shift ctrl to highlight a word at a time. Then ctrl + c and ctrl + v to copy and past respectively.  These are standard commands but do not work in a terminal. I assume there is some logical reason for this.  I would like equivalent if not the same abilities within a terminal

Ive been reading the manual for history and am not quite sure what it does yet.

Unrelated how do i get out of a manual in the terminal.  A number of times now i have pressed many buttons and finally given up and opened a new terminal.

---

### Post by Adramelech on 2007-03-30
1) move to the start of the text you want to copy
2) press Ctrl+spacekey
3) move to where you want to paste it and press Ctrl+Y

those are emacs like commands =).

---

### Post by zorkerz on 2007-03-30
Afraid i am missing something here.
Ive herd of emacs before but do not really understand.

Emacs are for the command line of the terminal only?

so i have the word nano for example
i put my cursor over the n press ctrl+space then move to where i want it copied and press ctrl+y.  Am i reading this wrong how do i select thThese text to be copied i could only have marked the beginning.

thanks

---

### Post by Adramelech on 2007-03-30
sorry about the emacs thing is just a reference, just forget about it.


Ctrl+space => set mark
Ctrl+W   => cut
Ctrl+Y  => paste

supposed you wrote in terminal:
"Im happy using Ubuntu"

and you want to copy the word "using".

Move the cursor to the letter "u" of "using", press ctr+space.   (set mark)
Move the cursor to the "g" of "using", press Ctrl+W  (Cut starting from lastmark)
Move the cursor to where you want to paste, press Ctrl+Y  (paste)

---

### Post by Particle on 2007-03-30
Alternately, you may copy and paste using the traditional key combos if you just add shift to it.

Ctrl+Shift+C = Copy
Ctrl+Shift+V = Paste

---

### Post by zorkerz on 2007-03-30
> **Adramelech said:**
> Ctrl+space => set mark
Ctrl+W   => cut
Ctrl+Y  => paste

is there copy rather than cut

ah emacs I see now [http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/)
never used before

---

### Post by bikeboy on 2007-03-30
edit: I should refresh the page before I post, my solution was offered.

---

### Post by zorkerz on 2007-03-30
yes adding the shift is also very helpful under some circumstances however get me if i am wrong it requires already highlighted text which must be done with the mouse?

---

### Post by Adramelech on 2007-03-30
Just cut it and paste it immediately, the text is still in the buffer to get pasted elsewhere

---

### Post by zorkerz on 2007-03-30
oh your right that would work nicely. Interesting how that cuts down on the number of commands needed by one.

---

