---
title: "Mapping Caps Lock in vi"
date: 2006-11-01
forum: General Help
---

### Post by tonyr1988 on 2006-11-01
This is what I'd want to do (ideally):

When using vi, it can be a pain to reach up and type the Esc key in order to change modes. Would it be possible to give the Caps Lock that function? The tricky part:

1) I only want it to happen when using vi. For all the other programs, Caps Lock should work like usual, and

2) If possible, I'd like for it to work when I'm ssh'ing into my school's servers and using vi there.

Is this is at possible?

---

### Post by marianom on 2006-11-01
I'm using vim so maybe this is no help but let's try:

in vim you have these "key mappings" where you can set same actions with a key, example (as read in the guide):
**:map <F2> GoDate: <Esc>:read !date<CR>kJ**
and its explanation:
"*This shows how three modes are used.  After going to the last line with "G", the "o" command opens a new line and starts Insert mode.  The text "Date: " is inserted and <Esc> takes you out of insert mode*."

Maybe you have a similar function in vi and you can set it to work as desired.
If you have vim installed you can check the guide (I have it @ usr/share/doc/vim-common). It's chaper *40.1* Key mapping

---

### Post by tonyr1988 on 2006-11-01
Sorry for not clarifying - I have vim, not vi (in both places, locally and ssh'ing). I'm just used to calling it vi, since that's the command I call. :P

I'm gonna check out that guide right now, but what would I need for the caps key? I see you have <F2>, <Esc>, etc. Can I use <Caps> or something similar?

It may be in the guide, I'll look now.

---

### Post by ryjac on 2006-11-02
i realize you want to use caps lock which is understandable, but i thought i would point out that ctl+[ is the same as esc and will pput you back in command mode.

before, i bound a; to esc and it worked great...except for the fact that i typed a; in every other editor that i used. :-/

---

### Post by marianom on 2006-11-02
Hi there,
I'm not sure if capslock is the right option. What would happen if you want to write a paragraph in upper? Keep shift pressed? 
Another thing: caps is not a key that triggers an action, it merely puts your keyboard in a certain state (allowing to type in upper) so I'm not sure it will accomplish what you're trying.

Try with map but consider another combination. With map it seems you can set in every vim session you're using (home or at the server) and it'll apply just to vim.

If you can't find the vim guide try with usr/share/doc/vim-common/html/help.html

---

