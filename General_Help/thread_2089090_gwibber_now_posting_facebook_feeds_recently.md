---
title: "gwibber now posting facebook feeds recently"
date: 2012-11-28
forum: General Help
---

### Post by dyetheskin on 2012-11-28
twitter refreshes and shows feeds just fine but facebook doesn't. if i use gwibber to post something for myself it shows up if I confirm it on my droid but it doesn't pull any data in gwibber. it's like working only in one direction. i checked proxy settings, tried removing and reinstalling. no go. removing and adding the account didn't work. i tried removing the access within facebook to re-auth as well. I'm using 12.10 64 bit version. gwibber version is 3.6

log shows the following

2012-11-28 05:45:46,239 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 05:45:46,239 - Service      MainThread    :  INFO     - Service starting
2012-11-28 05:45:46,239 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 05:45:46,510 - Dispatcher   MainThread    :  INFO     - Found account 3/twitter-microblog
2012-11-28 05:45:46,529 - Dispatcher   MainThread    :  INFO     - Found account 8/facebook-microblog
2012-11-28 05:45:46,529 - Dispatcher   MainThread    :  INFO     - Found 2 accounts
2012-11-28 05:45:48,434 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 05:45:48,434 - Service      MainThread    :  INFO     - Service starting
2012-11-28 05:45:48,434 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 05:45:48,553 - Service      MainThread    :  INFO     - Found gwibber-service already running, exiting
2012-11-28 05:45:53,881 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:45:53,881 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:45:53,885 - Dispatcher   MainThread    :  INFO     - Running Jobs: 5
2012-11-28 05:45:55,034 - Dispatcher   Thread-2      :  INFO     - Loading complete: 1 - 0
2012-11-28 05:45:55,336 - Dispatcher   Thread-1      :  INFO     - Loading complete: 2 - 1
2012-11-28 05:45:55,641 - Dispatcher   Thread-4      :  INFO     - Loading complete: 3 - 0
2012-11-28 05:45:55,644 - Dispatcher   Thread-3      :  INFO     - Loading complete: 4 - 0
2012-11-28 05:45:59,452 - Dispatcher   Thread-5      :  ERROR    - <facebook:receive> Operation failed
2012-11-28 05:45:59,462 - Dispatcher   Thread-5      :  INFO     - Loading Error: 4 - Error
2012-11-28 05:46:54,393 - Storage      MainThread    :  INFO     - Cleaning up database...
2012-11-28 05:46:54,394 - Storage      MainThread    :  INFO     - Found 63 records in the messages stream for account 3/twitter-microblog
2012-11-28 05:48:49,992 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 05:48:49,993 - Service      MainThread    :  INFO     - Service starting
2012-11-28 05:48:49,993 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 05:48:50,121 - Identica     MainThread    :  DEBUG    - Initializing.
2012-11-28 05:48:50,126 - Facebook     MainThread    :  DEBUG    - Initializing.
2012-11-28 05:48:50,131 - Twitter      MainThread    :  DEBUG    - Initializing.
2012-11-28 05:48:50,135 - Service      MainThread    :  DEBUG    - Setting up monitors
2012-11-28 05:48:50,139 - Dispatcher   MainThread    :  DEBUG    - NM Version is 0.9.6.0
2012-11-28 05:48:50,140 - Dispatcher   MainThread    :  DEBUG    - NM Version is greater than 0.8.997
2012-11-28 05:48:50,158 - Storage      MainThread    :  DEBUG    - Creating indexes
2012-11-28 05:48:50,183 - Dispatcher   MainThread    :  INFO     - Found account 3/twitter-microblog
2012-11-28 05:48:50,184 - Dispatcher   MainThread    :  INFO     - Found account 8/facebook-microblog
2012-11-28 05:48:50,184 - Dispatcher   MainThread    :  INFO     - Found 2 accounts
2012-11-28 05:49:00,351 - Dispatcher   MainThread    :  DEBUG    - Refresh interval is set to 5
2012-11-28 05:49:00,356 - Dispatcher   MainThread    :  DEBUG    - ** Starting Refresh - 2012-11-28 05:49:00.356820 **
2012-11-28 05:49:00,357 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:49:00,357 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:49:00,357 - Dispatcher   Thread-1      :  DEBUG    - <twitter:receive> Performing operation
2012-11-28 05:49:00,358 - Twitter      Thread-1      :  DEBUG    - Logging in
2012-11-28 05:49:00,361 - Dispatcher   Thread-2      :  DEBUG    - <twitter:responses> Performing operation
2012-11-28 05:49:00,362 - Dispatcher   Thread-3      :  DEBUG    - <twitter:private> Performing operation
2012-11-28 05:49:00,362 - Dispatcher   Thread-4      :  DEBUG    - <twitter:lists> Performing operation
2012-11-28 05:49:00,363 - Dispatcher   MainThread    :  INFO     - Running Jobs: 5
2012-11-28 05:49:00,363 - Dispatcher   Thread-5      :  DEBUG    - <facebook:receive> Performing operation
2012-11-28 05:49:00,366 - Facebook     Thread-5      :  DEBUG    - Logging in
2012-11-28 05:49:00,671 - Twitter      MainThread    :  DEBUG    - Login completed
2012-11-28 05:49:00,672 - Twitter      Thread-1      :  DEBUG    - User id is: 456559364, name is dyetheskin
2012-11-28 05:49:00,933 - Facebook     MainThread    :  DEBUG    - Login completed
2012-11-28 05:49:01,137 - Dispatcher   Thread-2      :  INFO     - Loading complete: 1 - 0
2012-11-28 05:49:01,141 - Dispatcher   Thread-1      :  INFO     - Loading complete: 2 - 0
2012-11-28 05:49:01,141 - Dispatcher   Thread-1      :  DEBUG    - <twitter:receive> Finished operation (0:00:00.784081)
2012-11-28 05:49:01,141 - Dispatcher   Thread-2      :  DEBUG    - <twitter:responses> Finished operation (0:00:00.780234)
2012-11-28 05:49:01,230 - Facebook     Thread-5      :  DEBUG    - User id is: 1336102312
2012-11-28 05:49:01,626 - Dispatcher   Thread-3      :  INFO     - Loading complete: 3 - 0
2012-11-28 05:49:01,626 - Dispatcher   Thread-3      :  DEBUG    - <twitter:private> Finished operation (0:00:01.264242)
2012-11-28 05:49:01,654 - Dispatcher   Thread-4      :  INFO     - Loading complete: 4 - 0
2012-11-28 05:49:01,654 - Dispatcher   Thread-4      :  DEBUG    - <twitter:lists> Finished operation (0:00:01.291690)
2012-11-28 05:49:08,004 - Facebook     Thread-5      :  DEBUG    - <STATS> facebook:receive account:8/facebook-microblog since:2012-11-18T05:49:00.364474 size:133247
2012-11-28 05:49:08,007 - Dispatcher   Thread-5      :  ERROR    - <facebook:receive> Operation failed
2012-11-28 05:49:08,008 - Dispatcher   Thread-5      :  DEBUG    - Traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gwibber/microblog/dispatcher.py", line 83, in run
    message_data = PROTOCOLS[account["service"]].Client(account)(opname, **args)
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 369, in __call__
    return getattr(self, opname)(**args)
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 393, in receive
    return [self._message(post) for post in data["data"]]
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 329, in _message
    m["privacy"]["description"] = data["privacy"]["description"]
KeyError: 'description'

2012-11-28 05:49:08,008 - Dispatcher   Thread-5      :  INFO     - Loading Error: 4 - Error
2012-11-28 05:49:08,008 - Dispatcher   Thread-5      :  DEBUG    - <facebook:receive> Finished operation (0:00:07.644800)
2012-11-28 05:50:00,396 - Storage      MainThread    :  INFO     - Cleaning up database...
2012-11-28 05:50:00,397 - Storage      MainThread    :  INFO     - Found 63 records in the messages stream for account 3/twitter-microblog
2012-11-28 05:54:00,446 - Dispatcher   MainThread    :  DEBUG    - Refresh interval is set to 5
2012-11-28 05:54:00,451 - Dispatcher   MainThread    :  DEBUG    - ** Starting Refresh - 2012-11-28 05:54:00.451818 **
2012-11-28 05:54:00,452 - Dispatcher   MainThread    :  INFO     - Running Jobs: 5
2012-11-28 05:54:00,452 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:54:00,452 - Dispatcher   Thread-6      :  DEBUG    - <twitter:receive> Performing operation
2012-11-28 05:54:00,453 - Twitter      Thread-6      :  DEBUG    - Re-authenticating
2012-11-28 05:54:00,454 - Dispatcher   Thread-8      :  DEBUG    - <twitter:private> Performing operation
2012-11-28 05:54:00,455 - Dispatcher   MainThread    :  INFO     - Running Jobs: 4
2012-11-28 05:54:00,454 - Dispatcher   Thread-9      :  DEBUG    - <facebook:receive> Performing operation
2012-11-28 05:54:00,455 - Dispatcher   Thread-7      :  DEBUG    - <twitter:responses> Performing operation
2012-11-28 05:54:00,746 - Twitter      MainThread    :  DEBUG    - Login completed
2012-11-28 05:54:00,746 - Twitter      Thread-6      :  DEBUG    - User id is: 456559364, name is dyetheskin
2012-11-28 05:54:00,747 - Twitter      Thread-7      :  DEBUG    - Re-authenticating
2012-11-28 05:54:01,023 - Twitter      MainThread    :  DEBUG    - Login completed
2012-11-28 05:54:01,023 - Twitter      Thread-7      :  DEBUG    - User id is: 456559364, name is dyetheskin
2012-11-28 05:54:01,024 - Twitter      Thread-8      :  DEBUG    - Re-authenticating
2012-11-28 05:54:01,263 - Dispatcher   Thread-6      :  DEBUG    - <twitter:receive> Adding record
2012-11-28 05:54:01,397 - Twitter      MainThread    :  DEBUG    - Login completed
2012-11-28 05:54:01,398 - Twitter      Thread-8      :  DEBUG    - User id is: 456559364, name is dyetheskin
2012-11-28 05:54:01,509 - Dispatcher   Thread-6      :  INFO     - Loading complete: 6 - 1
2012-11-28 05:54:01,509 - Dispatcher   Thread-6      :  DEBUG    - <twitter:receive> Finished operation (0:00:01.056582)
2012-11-28 05:54:01,526 - Dispatcher   Thread-7      :  INFO     - Loading complete: 6 - 0
2012-11-28 05:54:01,526 - Dispatcher   Thread-7      :  DEBUG    - <twitter:responses> Finished operation (0:00:01.070944)
2012-11-28 05:54:02,506 - Dispatcher   Thread-8      :  INFO     - Loading complete: 7 - 0
2012-11-28 05:54:02,506 - Dispatcher   Thread-8      :  DEBUG    - <twitter:private> Finished operation (0:00:02.052528)
2012-11-28 05:54:07,574 - Facebook     Thread-9      :  DEBUG    - <STATS> facebook:receive account:8/facebook-microblog since:2012-11-18T05:54:00.457334 size:133035
2012-11-28 05:54:07,575 - Dispatcher   Thread-9      :  ERROR    - <facebook:receive> Operation failed
2012-11-28 05:54:07,575 - Dispatcher   Thread-9      :  DEBUG    - Traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gwibber/microblog/dispatcher.py", line 83, in run
    message_data = PROTOCOLS[account["service"]].Client(account)(opname, **args)
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 369, in __call__
    return getattr(self, opname)(**args)
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 393, in receive
    return [self._message(post) for post in data["data"]]
  File "/usr/share/gwibber/plugins/facebook/__init__.py", line 329, in _message
    m["privacy"]["description"] = data["privacy"]["description"]
KeyError: 'description'

2012-11-28 05:54:07,576 - Dispatcher   Thread-9      :  INFO     - Loading Error: 7 - Error
2012-11-28 05:54:07,576 - Dispatcher   Thread-9      :  DEBUG    - <facebook:receive> Finished operation (0:00:07.121484)
2012-11-28 05:59:00,670 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 05:59:00,670 - Service      MainThread    :  INFO     - Service starting
2012-11-28 05:59:00,670 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 05:59:00,834 - Dispatcher   MainThread    :  INFO     - Found account 3/twitter-microblog
2012-11-28 05:59:00,835 - Dispatcher   MainThread    :  INFO     - Found account 9/facebook-microblog
2012-11-28 05:59:00,835 - Dispatcher   MainThread    :  INFO     - Found 2 accounts
2012-11-28 05:59:00,843 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:59:00,843 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 05:59:00,845 - Dispatcher   MainThread    :  INFO     - Running Jobs: 4
2012-11-28 05:59:01,646 - Dispatcher   Thread-2      :  INFO     - Loading complete: 1 - 0
2012-11-28 05:59:01,859 - Dispatcher   Thread-1      :  INFO     - Loading complete: 2 - 2
2012-11-28 05:59:02,127 - Dispatcher   Thread-3      :  INFO     - Loading complete: 3 - 0
2012-11-28 05:59:02,145 - Dispatcher   Thread-4      :  INFO     - Loading complete: 4 - 0
2012-11-28 06:00:01,352 - Storage      MainThread    :  INFO     - Cleaning up database...
2012-11-28 06:00:01,353 - Storage      MainThread    :  INFO     - Found 64 records in the messages stream for account 3/twitter-microblog
2012-11-28 06:04:01,352 - Dispatcher   MainThread    :  INFO     - Running Jobs: 4
2012-11-28 06:04:01,353 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:04:01,355 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:04:02,301 - Dispatcher   Thread-5      :  INFO     - Loading complete: 5 - 3
2012-11-28 06:04:02,904 - Dispatcher   Thread-7      :  INFO     - Loading complete: 6 - 0
2012-11-28 06:04:03,109 - Dispatcher   Thread-6      :  INFO     - Loading complete: 7 - 0
2012-11-28 06:09:01,359 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:09:01,359 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:09:01,361 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:09:02,438 - Dispatcher   Thread-8      :  INFO     - Loading complete: 9 - 1
2012-11-28 06:09:02,440 - Dispatcher   Thread-9      :  INFO     - Loading complete: 9 - 0
2012-11-28 06:09:03,350 - Dispatcher   Thread-10     :  INFO     - Loading complete: 10 - 0
2012-11-28 06:14:01,383 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:14:01,383 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:14:01,386 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:14:02,103 - Dispatcher   Thread-11     :  INFO     - Loading complete: 11 - 0
2012-11-28 06:14:02,568 - Dispatcher   Thread-12     :  INFO     - Loading complete: 12 - 0
2012-11-28 06:14:03,533 - Dispatcher   Thread-13     :  INFO     - Loading complete: 13 - 0
2012-11-28 06:19:01,352 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:19:01,352 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:19:01,357 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:19:02,077 - Dispatcher   Thread-14     :  INFO     - Loading complete: 14 - 0
2012-11-28 06:19:02,338 - Dispatcher   Thread-15     :  INFO     - Loading complete: 15 - 0
2012-11-28 06:19:03,199 - Dispatcher   Thread-16     :  INFO     - Loading complete: 16 - 0
2012-11-28 06:24:01,447 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:24:01,448 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:24:01,452 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:24:02,530 - Dispatcher   Thread-17     :  INFO     - Loading complete: 18 - 1
2012-11-28 06:24:02,551 - Dispatcher   Thread-18     :  INFO     - Loading complete: 18 - 0
2012-11-28 06:24:03,171 - Dispatcher   Thread-19     :  INFO     - Loading complete: 19 - 0
2012-11-28 06:29:01,434 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:29:01,434 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:29:01,440 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:29:02,429 - Dispatcher   Thread-20     :  INFO     - Loading complete: 20 - 1
2012-11-28 06:29:02,472 - Dispatcher   Thread-21     :  INFO     - Loading complete: 21 - 0
2012-11-28 06:29:03,324 - Dispatcher   Thread-22     :  INFO     - Loading complete: 22 - 0
2012-11-28 06:29:18,848 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:29:18,848 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:29:18,849 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:29:19,665 - Dispatcher   Thread-23     :  INFO     - Loading complete: 23 - 0
2012-11-28 06:29:19,842 - Dispatcher   Thread-24     :  INFO     - Loading complete: 24 - 0
2012-11-28 06:29:20,605 - Dispatcher   Thread-25     :  INFO     - Loading complete: 25 - 0
2012-11-28 06:32:36,235 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:32:36,235 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:32:36,241 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:32:37,050 - Dispatcher   Thread-26     :  INFO     - Loading complete: 26 - 0
2012-11-28 06:32:37,239 - Dispatcher   Thread-27     :  INFO     - Loading complete: 27 - 0
2012-11-28 06:32:37,979 - Dispatcher   Thread-28     :  INFO     - Loading complete: 28 - 0
2012-11-28 06:32:42,260 - Dispatcher   MainThread    :  INFO     - Gwibber Service is being shutdown
2012-11-28 06:32:45,064 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 06:32:45,064 - Service      MainThread    :  INFO     - Service starting
2012-11-28 06:32:45,064 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 06:32:45,245 - Dispatcher   MainThread    :  INFO     - Found account 3/twitter-microblog
2012-11-28 06:32:45,246 - Dispatcher   MainThread    :  INFO     - Found account 9/facebook-microblog
2012-11-28 06:32:45,246 - Dispatcher   MainThread    :  INFO     - Found 2 accounts
2012-11-28 06:32:55,351 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:32:55,352 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:32:55,358 - Dispatcher   MainThread    :  INFO     - Running Jobs: 4
2012-11-28 06:32:56,065 - Dispatcher   Thread-2      :  INFO     - Loading complete: 1 - 0
2012-11-28 06:32:56,089 - Dispatcher   Thread-1      :  INFO     - Loading complete: 2 - 0
2012-11-28 06:32:56,600 - Dispatcher   Thread-3      :  INFO     - Loading complete: 3 - 0
2012-11-28 06:32:56,605 - Dispatcher   Thread-4      :  INFO     - Loading complete: 4 - 0
2012-11-28 06:33:55,404 - Storage      MainThread    :  INFO     - Cleaning up database...
2012-11-28 06:33:55,405 - Storage      MainThread    :  INFO     - Found 66 records in the messages stream for account 3/twitter-microblog
2012-11-28 06:37:00,477 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 06:37:00,478 - Service      MainThread    :  INFO     - Service starting
2012-11-28 06:37:00,478 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 06:37:00,593 - Identica     MainThread    :  DEBUG    - Initializing.
2012-11-28 06:37:00,598 - Twitter      MainThread    :  DEBUG    - Initializing.
2012-11-28 06:37:00,604 - Service      MainThread    :  INFO     - Found gwibber-service already running, exiting
2012-11-28 06:37:47,596 - Dispatcher   MainThread    :  INFO     - Running Jobs: 4
2012-11-28 06:37:47,596 - Dispatcher   MainThread    :  INFO     - Running Jobs: 0
2012-11-28 06:37:47,598 - Dispatcher   MainThread    :  INFO     - Running Jobs: 3
2012-11-28 06:37:48,354 - Dispatcher   Thread-6      :  INFO     - Loading complete: 5 - 0
2012-11-28 06:37:48,619 - Dispatcher   Thread-5      :  INFO     - Loading complete: 6 - 0
2012-11-28 06:37:49,438 - Dispatcher   Thread-7      :  INFO     - Loading complete: 7 - 0
2012-11-28 06:37:51,341 - root         MainThread    :  INFO     - Logger initialized
2012-11-28 06:37:51,342 - Service      MainThread    :  INFO     - Service starting
2012-11-28 06:37:51,342 - Service      MainThread    :  INFO     - Running from the source tree
2012-11-28 06:37:51,468 - Identica     MainThread    :  DEBUG    - Initializing.
2012-11-28 06:37:51,473 - Twitter      MainThread    :  DEBUG    - Initializing.
2012-11-28 06:37:51,478 - Service      MainThread    :  INFO     - Found gwibber-service already running, exiting

---

### Post by dyetheskin on 2012-11-29
anyone have this working on 12.10 or can confim it's borked?

---

### Post by cdysthe on 2012-11-30
> **dyetheskin said:**
> anyone have this working on 12.10 or can confim it's borked?

Borked here also on Ubu 12.10 x64. No Facebook in Gwibber. Tried to delete and add the account again. No go. Twitter and Identi.ca works fine.

I have several of these in the gwibber log:

2012-11-30 13:31:04,352 - Dispatcher   Thread-289    :  ERROR    - <facebook:receive> Operation failed

---

### Post by dyetheskin on 2012-12-01
bumping this again

---

