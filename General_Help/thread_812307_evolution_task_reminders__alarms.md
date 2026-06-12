---
title: "evolution task reminders / alarms"
date: 2008-05-29
forum: General Help
---

### Post by dingfelder on 2008-05-29
One thing that I find annoyingly missing from Evolution is the ability to add an alarm / reminder to a task.

This functionality exists in both KOrganizer (KDE) and Windows Outlook so new users moving to Ubuntu may be annoyed to find it missing.

For me in particular, it is a show stopper as my father in law started using Ubuntu 8.04 and was able to accept the new system until he discovered this functionality was missing.  I now have had to revert him to windows because of this issue.

My thought is that if the evolution team does not want to add this feature, there is a back end evolution data store, and in theory a plug-in could query it and do the alarming independently.

Has anyone looked at this in more depth or have any bright ideas for getting an alarm to pop up for overdue tasks?

---

### Post by ddvanrooy on 2008-06-12
I feel exactly the same. It is a neat mailer but lacks decent pop-up reminders. O yes, I have seen them pop up if you (remember to) watch the screen just when they should come, but never again later.

I used Thunderbird for a while and had a plugin - ReminderFox - which was ok, but now for several reasons (upgraded to 8.04) I'm back with Evolution - and still fighting with reminders. 

I found a site : [http://www.gnomefiles.org/subcategory.php?sub_cat_id=75](http://www.gnomefiles.org/subcategory.php?sub_cat_id=75) with all sorts of plugins. The only thing is that I'm new in this game and REALLY struggle to install anything which isnt automagic

Cheers
D

---

### Post by Herman on 2008-06-21
:) There is a way to get Evolution to give you really great alarms but it's not documented sufficiently for most new users to be able to easily make use of the feature.

All you do is right-click on the Calendar in Evolution and select 'New Appointment'.
In the 'Appointment' window, fill in the fields as desired.
There's a 'Recurrence' button you can click on for another window for setting up the reminder to recur at whatever time intervals you want.

Now, the interesting part, the 'Alarm' button. Click on the 'Alarms' button and set the spinbox in the top of the 'Alarms' windows to 'customize'.
Click the 'Add' button to add an alarm.
Set the first spinbox to 'Run a program'.
Set the rest of the spinboxes as desired.

Now look at the 'Program' field. You can run any program you like to open or run any file you like in your /home/username directory. You can set totem to open an audio file and play you a song, and/or you can have gthumb open any image file for you.
*You can have your computer talk to you* with espeak, and if you're still worried about missing something, you can have the CD/DVD drawer open and close by itself to attract your attention. Almost anything is possible, your imagination is the only limit. :)

Programs I have tried include:
gthumb for opening image files (clip art, photos or any image files)
espeak for having the computer speak, for example: espeak 'your wifes birthday is coming up in a few days' (If you copy and paste that into a terminal it should work).
totem for playing music files, eg: totem Music/anysong.ogg
To open and close your CD/DVD drawer: eject ; eject -t

Add any of those commands to the 'Program' field in 'Add Alarm', once you've tested them in your terminal.
You can have any number of alarms for any appointment.

Something you need to be aware of is that Ubuntu will not run any programs from Evolution by itself the first time you try out each program. It will ask for your permission first. If you check the box for 'do not ask me about this program again', everything will work smoothly after the first time. As long as you give each program a test run you'll be fine, but make sure you do test each one before relying on it for anything important!

It will be a little better if a clever, kind and thoughtful programmer some day adds a way for a user to browse to find a file to be opened and can choose a program from a list or even have the program to open the fie with chosen automatically. For now we can already do whatever we want, it's just a wee bit more work than some users find attractive, but it's still quite doable, and we can do anything when we know how. :)

Have fun ! 
Regards, Herman :)

---

### Post by dingfelder on 2008-06-21
While I agree that you can create alarms for **appointments**, and like your writeup on improving alarms for appointments, the problem I am facing is the lack of alarms for **tasks**, not appointments.  

I have seen a number of similar complaints from other users while googling for an answer, so I guess this is a *known issue*, I'm just not sure if any Evolution developers care enough about this issue to address it.

Thanks for the feedback in any case.

Cheers,

Ding

---

### Post by Herman on 2008-06-21
:-k Oh, okay then, sorry for the confusion. 

Maybe you can help me instead then.
I was just taking a closer look yesterday in Evolution, and we can create three kinds of notes in Evolution; Calendar Appointments, Memos and Tasks.

What are the advantages and disadvantages of each? 
Why would we need all three?
When would we need a Memo when we can use a Task instead?
Why not just use Calendar Appointments for everything? 
What can we do with a Task that we can't do with a Calendar Appointment, (besides setting a custom alarm on it I mean)?

Regards, Herman :)

---

### Post by dingfelder on 2008-06-22
Here is my take on the differences:
appointments are for meetings etc and you can invite people, and set a
place etc.
you then view appts in a calendar.

tasks are "todos" like "pay the electricity bill"
typically, you create a task, and can view tasks in a todo list based
upon importance etc, and you can currently set a due date, after which
the color of the task changes.
The part that is missing is the pop-up reminder that the task is now overdue.

Tasks also have a "priority" that you can sort on 
and a completion status, and you can set them as 50% done etc.

I don't know about memos.

Basically, all 3 items are used for distinctly different purposes and all are needed.  The task vs appointment concept is pretty well defined across multiple different applications (Evolution, Outlook, Groupwise, & others) and users are quite used to the way they do things.

Clear as mud?

---

### Post by BenTX on 2011-08-12
It appears this is still an issue according to this [Bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=216130")

Since it's been awhile since the last reply, is there a 3rd party plugin or workaround for adding alarms/reminders to tasks?

Thanks!

---

