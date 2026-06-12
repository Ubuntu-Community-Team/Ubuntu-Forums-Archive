---
title: "Can't Type Curly Bracket with Left Shift"
date: 2020-06-17
forum: General Help
---

### Post by olivermc on 2020-06-17
So this is one of the wackier bugs I've run into in ten years of using Linux. I cannot type a curly bracket by holding down the left shift button and hitting the square bracket key. The left shift key works for all other circumstances. I can type square brackets without problem and I can type curly brackets with the right shift key. Using a USB Keyboard works fine. This is a problem in both the VTE and in X, so I don't think it's a keyboard shortcut, or at least not one in Gnome. xev doesn't register the keypress at all. Running setxkbmap with a variety of models makes no difference.

I'm running a Lenovo Thinkpad X1 Carbon. What on earth could be going on? I figure it has to be a hardware setting somewhere or some kind of hardware-level keyboard shortcut (is there such a thing?) but I can't figure out where it would be. Any help deeply appreciated!

---

### Post by Impavidus on 2020-06-17
So, what does xev tell you exactly? When you hit left_shift, it tells so, when you hit [, it tells so, but when you hit left_shift+[, it only reports the left_shift? Can you type { with left_shift+[ in a life session? It could be a hardware problem, I guess.

Some efficient keyboards can't handle every combination of characters as not every key has it's own wire attached. The electronics derive keypresses from combinations of wires, but that means some combinations of keys cannot be detected. I remember keyboards that couldn't handle left_arrow+up_arrow+left_shift, but a keyboard should always be able to handle such a basic combination as left_shift+[.

Am I correct that you use a keyboard with { = shift+[ , } = shift+] , both on the right side of the keyboard? For example, American layout.

---

### Post by ActionParsnip on 2020-06-17
Your curly brackets are called "braces" these are "{" and "}"
These are brackets "[" and "]"
These are parentheses "(" and ")"

---

### Post by olivermc on 2020-06-17
Thanks for the response. Yes this is a us-label keyboard. I've now noticed that it's also happening with the letter Y as well, so the mystery deepens. xev prints as expected for L Shift, square brackets, right shift, and right shift + Y, [, or ]. If I hold the key to be shifted and *the* press left shift, xev will actually show a keypress for the shifted key, although this doesn't print the character if I try to type it in a text box. 

I've actually now established that this is also happening in the BIOS keyboard diagnostic test, too, which means I don't think it can be an Ubuntu issue (unless it changed something in the EFI loader? Maybe?), but if you have any ideas at all I would love to hear them. It's just nutty.

---

### Post by Impavidus on 2020-06-18
Most likely a hardware problem, not something that can be fixed in software. There may be some crosstalk in the electronics of your keyboard that prevents registering some key combinations.

---

