---
title: "[ubuntu] Can't get pyo to work since JACK won't start"
date: 2016-02-27
forum: General Help
---

### Post by dah4pe on 2016-02-27
I'm trying to use the pyo python library, but I can't seem to get it working. Every time I try to import it I get this error

```
pyo version 0.7.8 (uses single precision)
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1514
Expression 'ValidateParameters( inputParameters, hostApi, StreamDirection_In )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2818
portaudio error in Pa_OpenStream: Invalid number of channels
Portaudio error: Invalid number of channels
Server not booted.
The Server must be booted!
Traceback (most recent call last):
  File "main.py", line 63, in <module>
    main()
  File "main.py", line 40, in main
    a = Sine(440, 0, 0.1).out()
  File "/usr/local/lib/python2.7/dist-packages/pyolib/generators.py", line 59, in __init__
    PyoObject.__init__(self, mul, add)
  File "/usr/local/lib/python2.7/dist-packages/pyolib/_core.py", line 562, in __init__
    PyoObjectBase.__init__(self)
  File "/usr/local/lib/python2.7/dist-packages/pyolib/_core.py", line 427, in __init__
    raise PyoServerStateException("The Server must be booted before creating any audio object.")
pyolib._core.PyoServerStateException: The Server must be booted before creating any audio object.
```


If I try to run JACK through qjackctl this is the message. 

```
 [COLOR=#999999]08:47:49.191 JACK is starting...[/COLOR]
 [COLOR=#990099]08:47:49.192 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server request channel[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]08:47:49.200 JACK was started with PID=19383.[/COLOR]
 [COLOR=#999999]Home directory not accessible: Permission denied[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]jackdmp 1.9.10[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2013 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#999999]Jack: JackPosixThread::StartImp : create non RT thread[/COLOR]
 [COLOR=#999999]Jack: JackPosixThread::ThreadHandler : start[/COLOR]
 [COLOR=#999999]Jack: playback device hw:0[/COLOR]
 [COLOR=#999999]Jack: capture device hw:0[/COLOR]
 [COLOR=#999999]Jack: apparent rate = 44100[/COLOR]
 [COLOR=#999999]Jack: frames per period = 1024[/COLOR]
 [COLOR=#999999]Jack: JackDriver::Open capture_driver_name = hw:0[/COLOR]
 [COLOR=#999999]Jack: JackDriver::Open playback_driver_name = hw:0[/COLOR]
 [COLOR=#999999]Jack: Check protocol client = 8 server = 8[/COLOR]
 [COLOR=#999999]Jack: JackEngine::ClientInternalOpen: name = system[/COLOR]
 [COLOR=#999999]Jack: JackEngine::AllocateRefNum ref = 0[/COLOR]
 [COLOR=#999999]Jack: JackPosixSemaphore::Allocate name = jack_sem.0_default_system val = 0[/COLOR]
 [COLOR=#999999]Jack: JackEngine::NotifyAddClient: name = system[/COLOR]
 [COLOR=#999999]Jack: JackGraphManager::SetBufferSize size = 1024[/COLOR]
 [COLOR=#999999]Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Jack: JackDriver::SetupDriverSync driver sem in flush mode[/COLOR]
 [COLOR=#999999]audio_reservation_init[/COLOR]
 [COLOR=#999999]Acquire audio card Audio0[/COLOR]
 [COLOR=#999999]creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#999999]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/COLOR]
 [COLOR=#999999]Jack: JackDriver::Close[/COLOR]
 [COLOR=#999999]Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Jack: JackEngine::ClientInternalClose ref = 0[/COLOR]
 [COLOR=#999999]Jack: JackEngine::ClientCloseAux ref = 0[/COLOR]
 [COLOR=#999999]Jack: JackGraphManager::RemoveAllPorts ref = 0[/COLOR]
 [COLOR=#999999]Jack: JackPosixSemaphore::Destroy name = jack_sem.0_default_system[/COLOR]
 [COLOR=#999999]Jack: ~JackDriver[/COLOR]
 [COLOR=#999999]Cannot initialize driver[/COLOR]
 [COLOR=#999999]Jack: no message buffer overruns[/COLOR]
 [COLOR=#999999]Jack: JackPosixThread::Stop[/COLOR]
 [COLOR=#999999]Jack: JackPosixThread::ThreadHandler : exit[/COLOR]
 [COLOR=#999999]JackServer::Open failed with -1[/COLOR]
 [COLOR=#999999]Jack: Succeeded in unlocking 82274202 byte memory area[/COLOR]
 [COLOR=#999999]Jack: JackShmMem::delete size = 0 index = 0[/COLOR]
 [COLOR=#999999]Jack: ~JackDriver[/COLOR]
 [COLOR=#999999]Jack: Succeeded in unlocking 1186 byte memory area[/COLOR]
 [COLOR=#999999]Jack: JackShmMem::delete size = 0 index = 1[/COLOR]
 [COLOR=#999999]Jack: Cleaning up shared memory[/COLOR]
 [COLOR=#999999]Jack: Cleaning up files[/COLOR]
 [COLOR=#999999]Jack: Unregistering server `default'[/COLOR]
 [COLOR=#999999]Failed to open server[/COLOR]
 [COLOR=#999999]08:47:49.339 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]08:47:51.317 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server request channel[/COLOR]

 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]


```

I've tried pretty much everything to get this working. I'm running Ubuntu 14.04 LTS. Python 2.7.6. I'm sure that PulseAudio is well and truly dead.

---

