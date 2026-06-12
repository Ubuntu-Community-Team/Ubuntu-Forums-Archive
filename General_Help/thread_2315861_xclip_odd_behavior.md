---
title: "xclip odd behavior"
date: 2016-03-03
forum: General Help
---

### Post by GrouchyGaijin on 2016-03-03
Hi Folks,


I have a script that uses xclip to copy the contents of a file.
The file has one line in it.  The line is overwritten with new information each time the script is run.

I had been using ```
[COLOR=black][FONT=Consolas]xclip [/FONT][/COLOR][COLOR=black][FONT=Consolas]-[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]in[/FONT][/COLOR][COLOR=black][FONT=Consolas]-[/FONT][/COLOR][COLOR=black][FONT=Consolas]selection c ~/file.txt[/FONT][/COLOR]
``` to get the information from the file into xclip.
That information is then pasted into the terminal using xdotool.

Recently, however, the information being pasted is not just the current contents of the file, but rather the current contents **plus** the former contents.

I checked the file xclip is copying and there is only one line in the file.  The information in the file is correct.
I thought perhaps that the problem might be in the paste action performed by xdotool, so I commented out that part of the script and tried by manually pasting into the terminal.

I get the same result.  The new correct information is pasted along with older out of date information.
It seems as if older text is being kept in a buffer and pasted along with the current text.

I have diodon installed, but I have restarted the computer with diodon disabled and I get the same behavior. 

My questions are:
Has anyone seen this happen before?
Could it be that somehow one of the clipboards (of the two or three built into Ubuntu) has become corrupt?  If so, is there a way to reset all the buffers?
I am not at home at the moment, but I can post the script this evening.

---

### Post by GrouchyGaijin on 2016-03-03
UPDATE

I think I found a work around.
Inserting ```
xsel -bc
``` at the start of the script seems to get rid of the problem, but I still do not understand why this would be necessary.

---

