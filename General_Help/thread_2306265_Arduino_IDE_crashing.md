---
title: "Arduino IDE crashing"
date: 2015-12-14
forum: General Help
---

### Post by ROVguy on 2015-12-14
Hey all,
I'm using Ubuntu 14.04 with Arduino 1:1.05+dfsg2-2.  

 Very often while I'm in the Arduino IDE the cursor starts selecting everything the way one would see if you left clicked and hold while dragging your mouse. If I click on the mouse all it does is restarts where the highlighing beginns. Restarting the Arduino IDE doesn't fix this. So far the only way to stop it is to restart Ubuntu.  This sometimes happens minutes after starting Ubuntu and Arduino IDE and sometimes an hour or longer after. 


 Is there something I need to install or update?  

 Thanks

---

### Post by QIII on 2015-12-14
Hello!

Your image was not properly added to the post.  Please use the attachment button (the paper clip) above the text input box to add images when posting.

To add it at this point, please select "Edit" and then "Go Advanced" to see the attachment button.

---

### Post by ROVguy on 2015-12-14
Hopefully the image uploaded this time.

---

### Post by brian-mccumber on 2015-12-14
Have you tried to use the up to date version of the Ardunio IDE? It looks like it's up to 1.6.6 now which will probably include alot of bug fixes from the version you are currently using. Unless you have to use that version for that particular board you are using you should try to update the IDE software.

---

### Post by ROVguy on 2015-12-15
I did look into that but the Ubuntu Software Centre doesn't have it yet. I'm using Ubuntu's latest stable version.

---

### Post by ROVguy on 2015-12-17
Since my last reply I have updated Ubuntu from 14.04.2 to 14.04.3. I didn't mention that I am using a Surface Pro 3 (maybe that matters). I have also installed the Arduino 1.6.6 IDE to try it out. 
Both versions of the IDE have frozen and would not respond to any commands. I did a computer reboot there.

On the 1.6.6 IDE I have not been able to get ros_lib examples installed and so anything to do with ROS is an error. Lastly highlighting has happened on this IDE.

On the 1:1.05+dfsg2-2 IDE I have had the highlighting happen but after eventually being able to close the program and reopen it the issue cleared. It seems to be happening less now but it is still happening.

Thanks.

---

### Post by ROVguy on 2015-12-17
I have discovered something new which might be the actual cause.
When I have these glitches they only affect the track pad on the key board but not the keyboard as I can still type and move around without issues using the arrow keys. I also noticed that the USB mouse does the same thing. The left and right button on the mouse don't work but the cursor moves around. 
So it almost seems like the software controlling the left and right click of the mouse/track pad has some sort of glitch and it keeps the button states high or ON. Should I start a new thread with regard to mouse and track pad issues?

Thanks

---

### Post by ROVguy on 2015-12-30
While continuing with this headache I noticed that the mouse and track pad button don't work only with the Arduino IDE. When the highlighting starts in the IDE I can't simply click on anything in the IDE like the X to close the app as it is unresponsive. While this is happening I can go to terminal, firefox, or a folder (that is all I have tried) and use the track pad buttons or mouse buttons without issue. At the same time I have also noticed that I can't connect to my Arduino board using rosserial once this starts. I keep getting a message that it can't connect and there could be an compatibility issue.

I'd really appreciate some suggestions.
Thanks

---

