---
title: "MythTV Aborted Recordings"
date: 2006-11-10
forum: General Help
---

### Post by fortytwo on 2006-11-10
Hey guys,
I've been setting up MythTV to record two shows which are back to back on the same channel, but every time Myth cancels the recording of the second show saying only "Canceled recording (aborted)"

When I look at the mythbackend log, I still don't get much information, but it does seem a bit funny (I've bolded the main events):

**2006-11-09 16:00:04.563 scheduler: Started recording: Scrubs "My Common Enemy": channel 1107 on cardid 1, sourceid 1**
0: start_time: 582.288 duration: 648.101
1: start_time: 582.241 duration: 648.114
stream: start_time: 6469.345 duration: 7201.645 bitrate=5189 kb/s
2006-11-09 16:00:04.622 AFD: Opened codec 0x82086e0, id(MPEG2VIDEO) type(Video)
2006-11-09 16:00:04.644 AFD: Opened codec 0x8208150, id(MP2) type(Audio)
2006-11-09 16:00:05.692 ret_pid(0) child(14362) status(0x0)
2006-11-09 16:00:06.732 ret_pid(0) child(14362) status(0x0)
2006-11-09 16:00:07.748 ret_pid(14362) child(14362) status(0x0)
2006-11-09 16:00:07.756 External Tuning program exited with no error
**2006-11-09 16:00:07.790 Finished recording Scrubs "My Common Enemy": channel 1107**
2006-11-09 16:00:07.799 scheduler: Finished recording: Scrubs "My Common Enemy": channel 1107
2006-11-09 16:00:07.928 Finished recording Scrubs "My Common Enemy": channel 1107
0: start_time: 1230.440 duration: 0.066
1: start_time: 1230.394 duration: 0.082
stream: start_time: 13671.049 duration: 1.243 bitrate=5102 kb/s
2006-11-09 16:00:07.972 AFD: Opened codec 0x8236980, id(MPEG2VIDEO) type(Video)
2006-11-09 16:00:07.982 AFD: Opened codec 0x8238820, id(MP2) type(Audio)
2006-11-09 16:00:08.012 TVRec(1): RingBufferChanged()
2006-11-09 16:00:08.031 Finished recording Scrubs "My Common Enemy": channel 1107
2006-11-09 16:00:08.209 New DB connection, total: 4
2006-11-09 16:00:08.225 Connected to database 'mythconverg' at host: localhost
**2006-11-09 16:02:35.846 Expiring Scrubs "My Common Enemy" from Thu Nov 9 16:00:00 2006, 0 MBytes, forced expire (LiveTV recording)**
2006-11-09 16:02:35.853 autoexpire: Expiring Program: Expiring Scrubs "My Common Enemy" from Thu Nov 9 16:00:00 2006, 0 MBytes, forced expire (LiveTV recording)
2006-11-09 16:29:29.399 TVRec(1): ASK_RECORDING 1 29 1
2006-11-09 16:30:00.701 TVRec(1): Enabling Full LiveTV UI.
2006-11-09 16:30:03.088 Finished recording Scrubs "My Common Enemy": channel 1107
**2006-11-09 16:30:03.097 JobQueue: Commercial Flagging Starting for Scrubs "My Common Enemy" recorded from channel 1107 at Thu Nov 9 16:00:00 2006**
2006-11-09 16:30:03.283 TVRec(1): Enabling Full LiveTV UI.
2006-11-09 16:30:03.448 commflag: Commercial Flagging Starting: Scrubs "My Common Enemy" recorded from channel 1107 at Thu Nov 9 16:00:00 2006
0: start_time: 1230.557 duration: 161.853
1: start_time: 1230.515 duration: 161.870
stream: start_time: 13672.393 duration: 1798.829 bitrate=5191 kb/s
2006-11-09 16:30:03.499 AFD: Opened codec 0x82b5a70, id(MPEG2VIDEO) type(Video)
2006-11-09 16:30:03.722 TVRec(1): RingBufferChanged()
2006-11-09 16:30:03.723 AFD: Opened codec 0x8264120, id(MP2) type(Audio)
[B]2006-11-09 16:30:03.468 Canceled recording (Aborted): Scrubs "My Last Chance": channel 1107 on cardid 1, sourceid 1
2006-11-09 16:30:04.261 Finished recording Scrubs "My Common Enemy": channel 1107
2006-11-09 16:30:04.326 scheduler: Last message repeated 3 times: Finished recording: Scrubs "My Common Enemy": channel 1107
2006-11-09 16:30:04.599 scheduler: Canceled recording (Aborted): Scrubs "My Last Chance": channel 1107 on cardid 1, sourceid 1
[/B]
First of all, the recording of the first episode seems a bit strange (starting the recording, then "finishing" it about 7 seconds later? Then expiring it? Then, after it says it finishes recording, it starts the commercial flagging, then cancels the next episode, then says it's finished recording the first episode, even though it already said it had?

Any ideas here guys? I'm a bit lost

Thanks

---

### Post by superm1 on 2006-11-11
From the way that is looking, these are livetv recordings?  Have you tried to schedule them directly through the scheduler?

---

### Post by fortytwo on 2006-11-11
They actually are done through the scheduler, not sure why the log (or mythtv) thinks they're live tv.

---

### Post by superm1 on 2006-11-12
Okay, from the looks of it - you had the livetv UI enabled when you had these recordings scheduled.  Do you have multiple tuners by chance?  See if this is consistently happening for both tuners when live tv UI is enabled or disabled.  In reality it shouldnt happen either way, but I don't trust that live tv myself either :)

---

### Post by fortytwo on 2006-11-12
Can you be a bit more specific when you say I 'have the livetv UI enabled'?  I do leave it on some channel whenever I turn the tv off, so I suppose it does think it's in live tv...but that shouldn't be a problem, should it?  Also...I've only got one tuner.

---

### Post by superm1 on 2006-11-13
Well, there shouldn't be problem with leaving it on live tv and turning off the tv, but I'm juts trying to eliminate this from the possibilities that it can be.  Try just hanging out in the menu when both recordings are supposed to happen, and then let it do them normally without being in live tv mode.

---

### Post by fortytwo on 2006-11-14
I'm trying to leave myth on a different menu other than the live, I'll see how it does this week to see if it's working.  But hopefully I won't have to do this in order to fix the problem.

---

### Post by superm1 on 2006-11-14
Well by no means will this be a necessary solution, but it helps to narrow down where the real issue lies.

---

