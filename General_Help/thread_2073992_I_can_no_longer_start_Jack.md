---
title: "I can no longer start Jack"
date: 2012-10-20
forum: General Help
---

### Post by Sableyes on 2012-10-20
Hello

I have been using Jack and IDJC too DJ for ages. I have always had too start Jack before any sound apps come on or it doesnt work. Even if I race my PC now, I no longer seem to be able too turn on Jack.

This is the code I get :

```
21:51:03.403 Patchbay deactivated.
21:51:03.437 Statistics reset.
21:51:03.530 ALSA connection change.
21:51:03.724 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:51:03.773 ALSA connection graph change.
21:51:07.408 Startup script...
21:51:07.409 artshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: 1: artshell: not found
21:51:07.814 Startup script terminated with exit status=32512.
21:51:08.089 D-BUS: JACK server could not be started. Sorry
Sat Oct 20 21:51:07 2012: Starting jack server...
Sat Oct 20 21:51:07 2012: JACK server starting in realtime mode with priority 1
Sat Oct 20 21:51:07 2012: Jack: Create non RT thread
Sat Oct 20 21:51:07 2012: Jack: ThreadHandler: start
Sat Oct 20 21:51:07 2012: Jack: playback device hw:0,0
Sat Oct 20 21:51:07 2012: Jack: capture device hw:0,0
Sat Oct 20 21:51:07 2012: Jack: apparent rate = 44100
Sat Oct 20 21:51:07 2012: Jack: frames per period = 128
Sat Oct 20 21:51:07 2012: Jack: JackDriver::Open capture_driver_name = hw:0,0
Sat Oct 20 21:51:07 2012: Jack: JackDriver::Open playback_driver_name = hw:0,0
Sat Oct 20 21:51:07 2012: Jack: Check protocol client = 8 server = 8
Sat Oct 20 21:51:07 2012: Jack: JackEngine::ClientInternalOpen: name = system
Sat Oct 20 21:51:07 2012: Jack: JackEngine::AllocateRefNum ref = 0
Sat Oct 20 21:51:07 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Sat Oct 20 21:51:07 2012: Jack: JackEngine::NotifyAddClient: name = system
Sat Oct 20 21:51:07 2012: Jack: JackGraphManager::SetBufferSize size = 128
Sat Oct 20 21:51:07 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Sat Oct 20 21:51:07 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Sat Oct 20 21:51:07 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Sat Oct 20 21:51:07 2012: control device hw:0
Sat Oct 20 21:51:07 2012: control device hw:0
Sat Oct 20 21:51:07 2012: Acquired audio card Audio0
Sat Oct 20 21:51:07 2012: creating alsa driver ... hw:0,0|hw:0,0|128|2|44100|0|0|nomon|swmeter|-|32bit
Sat Oct 20 21:51:07 2012: control device hw:0
Sat Oct 20 21:51:08 2012: [1m[31mERROR: 
ATTENTION: The playback device "hw:0,0" is already in use. Please stop the application using it and run JACK again[0m
Sat Oct 20 21:51:08 2012: Jack: JackDriver::Close
Sat Oct 20 21:51:08 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Sat Oct 20 21:51:08 2012: Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Sat Oct 20 21:51:08 2012: Jack: JackEngine::ClientCloseAux ref = 0
Sat Oct 20 21:51:08 2012: Jack: JackGraphManager::RemoveAllPorts ref = 0
Sat Oct 20 21:51:08 2012: Jack: JackPosixSemaphore::Destroy name = jack_sem.1000_default_system
Sat Oct 20 21:51:08 2012: Jack: ~JackDriver
Sat Oct 20 21:51:08 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Oct 20 21:51:08 2012: Jack: no message buffer overruns
Sat Oct 20 21:51:08 2012: Jack: JackPosixThread::Stop
Sat Oct 20 21:51:08 2012: Jack: ThreadHandler: exit
Sat Oct 20 21:51:08 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Oct 20 21:51:08 2012: Jack: Succeeded in unlocking 82246176 byte memory area
Sat Oct 20 21:51:08 2012: Jack: JackShmMem::delete size = 0 index = 0
Sat Oct 20 21:51:08 2012: Jack: ~JackDriver
Sat Oct 20 21:51:08 2012: Jack: Succeeded in unlocking 1040 byte memory area
Sat Oct 20 21:51:08 2012: Jack: JackShmMem::delete size = 0 index = 1
Sat Oct 20 21:51:08 2012: Jack: cleaning up shared memory
Sat Oct 20 21:51:08 2012: Jack: cleaning up files
Sat Oct 20 21:51:08 2012: Jack: unregistering server `default'
Sat Oct 20 21:51:08 2012: [1m[31mERROR: Failed to open server[0m
Sat Oct 20 21:51:09 2012: Saving settings to "/home/mutty/.config/jack/conf.xml" ...
21:51:11.697 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

I always have my set up the Naiux way :
[http://naiux.wordpress.com/2010/03/20/idjc-shoutcast-setup-guide/](http://naiux.wordpress.com/2010/03/20/idjc-shoutcast-setup-guide/)

Same on my partners PC too, and our cheapy box. Anyone got any ideas?

Thanks

---

