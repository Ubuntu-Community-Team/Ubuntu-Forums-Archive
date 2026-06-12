---
title: "How do I find the full path of a file when looking at the trancated properties"
date: 2014-03-24
forum: General Help
---

### Post by Robbyx on 2014-03-24
As there is no button to expand the file path, sometimes it is difficult to know the full path. Is there a shortuct or something else to have the properties show the full path?

---

### Post by TheFu on 2014-03-24
Which program r u using?
From the terminal it is easy - use **locate** or **which** CLI tools. "which" only works for programs in the PATH.

---

### Post by Robbyx on 2014-03-24
Typically I am using a file manager. The file will be a linked file and I look at the properties to see where is   the  target file. It is in the link's properties that I see a trancated version of the path to the original.

---

### Post by papibe on 2014-03-24
Hi Robbyx.

If you are referring to a way to see the path of the file in the file manager (called Nautilus), right click the file, and select properties.

A new window will open, with the field 'Location'. The full path will be then: Location + Name

Does that help?
Regards.

---

### Post by Robbyx on 2014-03-24
I am not seeing the full path. It is trancated in the middle. I see only the beginning and end of the path with centre replaced by dots.

---

### Post by mc4man on 2014-03-24
have you tried making the properties window bigger (longer l > r

---

### Post by papibe on 2014-03-24
Another alternative is to press Ctrl+L so that the current path appears on the proper Nautilus windows. It would be even selected so you can copy/paste it if you want.

Pressing Esc would make the path disappear again.

Regards.

---

### Post by Robbyx on 2014-03-24
Yes. The file properties do  not stretch.

BTW I am looking at the file properties of a symbolic link. Both the location and the target are very abbreviated in the file properties.

---

### Post by mc4man on 2014-03-24
> **Robbyx said:**
> Yes. The file properties do  not stretch.

BTW I am looking at the file properties of a symbolic link. Both the location and the target are very abbreviated in the file properties.

What release of Ubuntu are you using & is your screen 'really' small?
 At least here the nautilus properties window can either be pulled larger or maximized. In either case I've yet to find a location path that doesn't fit the window (expand from truncated ... to full. (15" screen here

edit: don't see any real limit here as prop window can be 'streched' beyound workspace.
In any event, any truncated  path, if copied then pasted into a text docu or terminal will also show the complete path

---

### Post by Robbyx on 2014-03-24
I now understand what has happened. I use PCMan as a file manager. In the version  i have the file properties do not stretch. I can confirm they do stretch in Nautilus. Shame because I prefer PCMan.

---

### Post by mc4man on 2014-03-24
> **Robbyx said:**
> I now understand what has happened. I use PCMan as a file manager. In the version  i have the file properties do not stretch. I can confirm they do stretch in Nautilus. Shame because I prefer PCMan.
Have you tried highlighting the truncated location, copying  & seeing if it pastes the full path?
(if pcman allows copy in prop. window...

---

### Post by Robbyx on 2014-03-25
> **mc4man said:**
> Have you tried highlighting the truncated location, copying  & seeing if it pastes the full path?
(if pcman allows copy in prop. window...
Copying and pasting does work and it shows the full path. Thanks. 
The only problem is I have to open up a program to paste in the results just to see the full path, but at least I now have two approaches: yours and the idea of using Nautilus.

---

### Post by whitesmith on 2014-03-25
> **Robbyx said:**
> I now understand what has happened. I use PCMan as a file manager. In the version  i have the file properties do not stretch. I can confirm they do stretch in Nautilus. Shame because I prefer PCMan.No matter what file manager you are using the Run Application Trick is at your service. Just open Run Application (Alt+F2) and drap-and-drop the file into the window. Voila!

---

### Post by Dave_L on 2014-03-25
> **Robbyx said:**
> Copying and pasting does work and it shows the full path. Thanks. 
The only problem is I have to open up a program to paste in the results just to see the full path, but at least I now have two approaches: yours and the idea of using Nautilus.

The file manager Thunar, like Nautilus, shows the full path. It's a compromise between Nautilus and PCManFM.

Another approach is to keep a terminal window open all the time, as I like to do.

---

### Post by Robbyx on 2014-03-25
> No matter what file manager you are using the Run Application Trick is at your service. Just open Run Application (Alt+F2) and drap-and-drop the file into the window. Voila! 

How do you get round the problem of the Run Application window closing immediately I change focus to the file manager. This happens with both Nautilus and PCMan?

---

