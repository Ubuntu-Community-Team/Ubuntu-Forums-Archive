---
title: "Google hangout high load"
date: 2014-03-18
forum: General Help
---

### Post by gabbello on 2014-03-18
Hello,

I have a lenovo X1 laptop with i7 processor and 8 GB of RAM. I have installed on it ubuntu 13.10 + xfce.

Whenever I start google hangout the load goes up very fast and eventuallly system becomes non-responsive and I have the reboot.

See below the output of top command when I started a single hangout call (just with myself in it)

```
top - 12:14:37 up 56 min,  3 users,  load average: 3,42, 1,11, 0,59
Tasks: 209 total,   3 running, 206 sleeping,   0 stopped,   0 zombie
%Cpu0  : 80,1 us, 13,2 sy,  0,0 ni,  6,4 id,  0,0 wa,  0,0 hi,  0,3 si,  0,0 st
%Cpu1  : 84,4 us,  9,5 sy,  0,0 ni,  6,1 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
%Cpu2  : 75,3 us, 17,6 sy,  0,0 ni,  7,1 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
%Cpu3  : 75,3 us, 16,2 sy,  0,0 ni,  8,1 id,  0,0 wa,  0,0 hi,  0,3 si,  0,0 st
KiB Mem:   8057048 total,  3030660 used,  5026388 free,   107024 buffers
KiB Swap:  8267772 total,        0 used,  8267772 free,  1080820 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND          
 5714 gp        20   0 1241m 146m  36m S 228,1  1,9   2:05.20 GoogleTalkPlugi  
 5690 gp        20   0 1381m 293m  53m R  47,8  3,7   0:39.43 chrome           
 5673 gp        20   0  445m  57m  37m S  28,6  0,7   0:18.19 chrome      

```


The load seems to go done a lot if I turn down my webcam, but still in a longer conference I would experience increase of loads and in the end disconection/non-responsive system even with webcam turned off.

Note that I've installed chrome hangout plugin and I start it by going to google plus page and click Hangouts tab (so it starts inside chrome), on another linux laptop I remebered that hangout actually was an independent app. (that was started when I started chrome), but I was not able to install it this way now.

---

### Post by gabbello on 2014-03-18
Follwoing instructions form here: [https://support.google.com/a/answer/2978955?hl=en](https://support.google.com/a/answer/2978955?hl=en)

I managed to capture hangout logs:

```
[000:000] Cpu: 6.42.7, x4, 2801Mhz, 7868MB
[000:000] Computer model: Not available
[000:007] Read port file, port=50225
[000:007] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[000:009] 0x7fab69798700:  sending cookie lQ+Kb5u3PZD1FB2i
[000:009] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[000:010] 0x7fab6977e510: Initiated connection to GoogleTalkPlugin
[000:105] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "error" : 111,
        "step" : "4"
    }
]

[000:225] Warning(clientchannel.cc:610): 0x7fab6977e510: Connection to GoogleTalkPlugin failed, reason=111
[000:225] Flute processes.
[000:227] Warning(clientchannel.cc:756): 0x7fab6977e510: Stale port file; attempting to restart flute.
[000:327] Read port file, port=50225
[000:327] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[000:328] 0x7fab697988c0:  sending cookie lQ+Kb5u3PZD1FB2i
[000:328] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[000:329] 0x7fab6977e5a0: Initiated connection to GoogleTalkPlugin
[000:329] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "error" : 111,
        "step" : "4"
    }
]

[000:329] Warning(clientchannel.cc:610): 0x7fab6977e5a0: Connection to GoogleTalkPlugin failed, reason=111
[000:329] Flute processes.
[000:331] Warning(clientchannel.cc:756): 0x7fab6977e5a0: Stale port file; attempting to restart flute.
[001:229] 0x7fab6977e510: Restarting GoogleTalkPlugin...
[001:230] Starting Flute
[001:230] Warning(pluginutils.cc:268): Failed to get GoogleTalkPlugin path. Trying default.
[001:231] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[001:231] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "2"
    }
]

[001:239] 0x7fab6977e510: Waiting for GoogleTalkPlugin to start...
[001:428] 0x7fab6977e5a0: Restarting GoogleTalkPlugin...
[001:428] Starting Flute
[001:429] Warning(pluginutils.cc:268): Failed to get GoogleTalkPlugin path. Trying default.
[001:438] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[001:438] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "2"
    }
]

[001:447] 0x7fab6977e5a0: Waiting for GoogleTalkPlugin to start...
[002:248] 0x7fab6977e510: Attempting to connect to GoogleTalkPlugin...
[002:249] Read port file, port=41607
[002:249] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[002:251] 0x7fab69798700:  sending cookie fjE4AaYRluOwzDaC
[002:251] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[002:252] 0x7fab6977e510: Initiated connection to GoogleTalkPlugin
[002:329] 0x7fab6977e510: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "3"
    }
]

[002:330] 0x7fab6977e510: Socket connection established
[002:331] 0x7fab6977e510: ScheduleOnlineCheck: Online check in 5000ms
[002:349] 0x7fab69798700: Got cookie response, socket is authorized
[002:349] 0x7fab6977e510: AUTHORIZED; socket handshake complete
[002:354] 0x7fab6977e510: C->F: ["mf",2,{"appName":"homepage","buildLabel":"chat_wcs_20140310.133048_RC1","setup_timeout":90000,"exps":["mef","tm","tl","fcom","cpuadaptation","vp","mtg","wvlb","ols","ia","wvhb","pocm","fcaq","fcas","wvls","hre","bpd","wvlm","hc","wv","spar","vnr","msv","gii","cc"],"jid":"gabbello@gmail.com","renderer":2,"useBrowserHttp":true,"o3dVersion":"0.1.44.29","domain":"talkgadget.google.com","useragent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36","pluginversion":"5.1.5.0"}]
[002:357] 0x7fab6977e510: F->C: ["fs",{"pr":"a"}]
[002:429] 0x7fab6977e510: F->C: ["mf","mf5.1","5.1.5.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Integrated Camera","caps":15,"cpuAdaptVersion":1,"cpuArchitecture":1,"cpuCacheSize":4194304,"cpuFamily":6,"cpuFlags":["sse2","ssse3","sse4_1","sse4_2","avx"],"cpuHasSSE2":true,"cpuModel":42,"cpuSpeed":2801,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":4,"cpusPhysical":2,"cryptoRandom":"OnVZrtJEhl5iLHYNr34BpDyy","cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":11,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":1,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[100,"VP8",640,400,30],[116,"red",640,400,30],[117,"ulpfec",640,400,30],[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"},{"id":3,"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time"}],"vsVersion":1}]
[002:442] 0x7fab6977e510: C->F: ["getdevicestate"]
[002:443] 0x7fab6977e510: F->C: ["getproxyforurl",{"url":"https://relay.google.com/"}]
[002:443] Error(clientchannel.cc:551): 0x7fab6977e510: Failed getting proxy settings: ["getproxyforurl",{"url":"https://relay.google.com/"}]
[002:449] 0x7fab6977e5a0: Attempting to connect to GoogleTalkPlugin...
[002:449] Read port file, port=41607
[002:449] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[002:450] 0x7fab697988c0:  sending cookie fjE4AaYRluOwzDaC
[002:450] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[002:451] 0x7fab6977e5a0: Initiated connection to GoogleTalkPlugin
[002:529] 0x7fab6977e510: F->C: ["getdevicestate","15","1",["__default_device","Plantronics .Audio 655 DSP Analog Stereo"],"2",["__default_device","Built-in Audio Digital Stereo (HDMI)","Plantronics .Audio 655 DSP Analog Stereo"],"0",["Integrated Camera"]]
[002:532] 0x7fab6977e5a0: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "3"
    }
]

[002:533] 0x7fab6977e5a0: Socket connection established
[002:533] 0x7fab6977e5a0: ScheduleOnlineCheck: Online check in 5000ms
[002:549] 0x7fab697988c0: Got cookie response, socket is authorized
[002:549] 0x7fab6977e5a0: AUTHORIZED; socket handshake complete
[002:555] 0x7fab6977e5a0: C->F: ["mf",2,{"jid":"gabbello@gmail.com","domain":"plus.google.com","useragent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36","pluginversion":"5.1.5.0"}]
[002:556] 0x7fab6977e5a0: F->C: ["fs",{"pr":"a"}]
[002:630] 0x7fab6977e5a0: F->C: ["mf","mf5.1","5.1.5.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Integrated Camera","caps":15,"cpuAdaptVersion":1,"cpuArchitecture":1,"cpuCacheSize":4194304,"cpuFamily":6,"cpuFlags":["sse2","ssse3","sse4_1","sse4_2","avx"],"cpuHasSSE2":true,"cpuModel":42,"cpuSpeed":2801,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":4,"cpusPhysical":2,"cryptoRandom":"jbesRtfWec54wTPT3TjOBVOM","cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":11,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":1,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[100,"VP8",640,400,30],[116,"red",640,400,30],[117,"ulpfec",640,400,30],[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"},{"id":3,"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time"}],"vsVersion":1}]
[007:335] 0x7fab6977e510: HandleOnlineCheck: Starting check
[007:335] 0x7fab6977e510: HandleOnlineCheck: OK; current state: 3
[007:535] 0x7fab6977e5a0: HandleOnlineCheck: Starting check
[007:536] 0x7fab6977e5a0: HandleOnlineCheck: OK; current state: 3
[044:026] Read port file, port=41607
[044:026] 0x7fab6977e360: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[044:027] 0x7fab69798000:  sending cookie fjE4AaYRluOwzDaC
[044:027] 0x7fab6977e360: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[044:027] 0x7fab6977e360: Initiated connection to GoogleTalkPlugin
[044:084] 0x7fab6977e360: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "3"
    }
]

[044:125] 0x7fab6977e360: Socket connection established
[044:125] 0x7fab6977e360: ScheduleOnlineCheck: Online check in 5000ms
[044:126] 0x7fab69798000: Got cookie response, socket is authorized
[044:126] 0x7fab6977e360: AUTHORIZED; socket handshake complete
[044:133] 0x7fab6977e360: C->F: ["mf",2,{"jid":"gabbello@gmail.com","exps":["gii","bpd","wvls","msv","wv","tm","wvlb","spar","fcas","hre","ols","pocm","fcom","hc","wvlm","mef","cc","ia","fcaq","vnr","tl","wvhb","cpuadaptation"],"domain":"plus.google.com","useragent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36","pluginversion":"5.1.5.0"}]
[044:134] 0x7fab6977e360: F->C: ["fs",{"pr":"a"}]
[044:225] 0x7fab6977e360: F->C: ["mf","mf5.1","5.1.5.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Integrated Camera","caps":15,"cpuAdaptVersion":1,"cpuArchitecture":1,"cpuCacheSize":4194304,"cpuFamily":6,"cpuFlags":["sse2","ssse3","sse4_1","sse4_2","avx"],"cpuHasSSE2":true,"cpuModel":42,"cpuSpeed":2801,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":4,"cpusPhysical":2,"cryptoRandom":"rKbTbnmq/fffT78U+QrpEGWx","cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":11,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":1,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[100,"VP8",640,400,30],[116,"red",640,400,30],[117,"ulpfec",640,400,30],[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"},{"id":3,"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time"}],"vsVersion":1}]
[044:229] 0x7fab6977e360: F->C: ["getproxyforurl",{"url":"https://relay.google.com/"}]
[044:229] Error(clientchannel.cc:551): 0x7fab6977e360: Failed getting proxy settings: ["getproxyforurl",{"url":"https://relay.google.com/"}]
[044:607] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[044:610] 0x7fab6977e360: C->F: ["streamon","jid","preview","o1d2638-2",34,null,1280,720]
[044:975] 0x7fab6977e360: C->F: ["mf",2,{"appName":"hangout","buildLabel":"chat_wcs_20140310.133048_RC1","allowConcurrentSessions":"true","typing":{"mute_timeout":1250,"time_window":0,"cost_per_typing":0,"reporting_threshold":0,"penalty_decay":0,"type_event_delay":2,"min_participants":100},"cams":[{"usbid":"046d:0809","w":640,"h":480,"fps":30},{"usbid":"046d:09a6","w":640,"h":480,"fps":30},{"usbid":"046d:08ca","w":640,"h":480,"fps":30},{"usbid":"046d:0990","w":640,"h":480,"fps":30},{"usbid":"17ef:480f","w":640,"h":480,"fps":30},{"usbid":"5986:02d5","w":640,"h":480,"fps":30},{"name":"MT9M114","w":640,"h":480,"fps":30},{"usbid":"05ac:8507","w":640,"h":480,"fps":30},{"usbid":"05ac:850a","w":640,"h":480,"fps":30},{"usbid":"05ac:8509"},{"usbid":"05ac:8510"},{"usbid":"046d:0823"},{"usbid":"046d:0821"},{"usbid":"046d:082d"},{"usbid":"046d:0843"},{"usbid":"046d:082c"},{"usbid":"046d:0826"},{"usbid":"046d:081d"},{"usbid":"046d:081b"},{"usbid":"046d:0825"},{"usbid":"045e:075d"},{"usbid":"045e:0772"},{"name":"Pan Tilt Zoom Camera"},{"name":"AJA SDI input"},{"name":"AJA HDMI input"},{"usbid":"04f2:b2a4"},{"usbid":"0839:1095"},{"usbid":"0ac8:3530"},{"usbid":"5555:3411"},{"usbid":"1778:0204"},{"usbid":"1778:0206"}],"exps":["mpi","mef","tm","tl","fcom","cpuadaptation","vp","mtg","wvlb","ols","ia","wvhb","pocm","fcaq","fcas","wvls","hre","bpd","wvlm","hc","wv","spar","vnr","msv","gii","cc"],"jid":"gabbello@gmail.com","renderer":2,"useBrowserHttp":true,"o3dVersion":"0.1.44.29","domain":"plus.google.com","useragent":"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36","pluginversion":"5.1.5.0"}]
[044:985] 0x7fab6977e360: F->C: ["mf","mf5.1","5.1.5.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Integrated Camera","caps":15,"cpuAdaptVersion":1,"cpuArchitecture":1,"cpuCacheSize":4194304,"cpuFamily":6,"cpuFlags":["sse2","ssse3","sse4_1","sse4_2","avx"],"cpuHasSSE2":true,"cpuModel":42,"cpuSpeed":2801,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":4,"cpusPhysical":2,"cryptoRandom":"8zRIIjyHSd4CM8PqY5RyhQmU","cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":11,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":1,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[100,"VP8",640,400,30],[116,"red",640,400,30],[117,"ulpfec",640,400,30],[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"},{"id":3,"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time"}],"vsVersion":1}]
[045:068] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[045:069] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":true}]
[045:074] 0x7fab6977e360: C->F: ["comment","CSI sessionId: 4be92f248af237c5e60d09749ef12fd4"]
[045:076] 0x7fab6977e360: C->F: ["getdevicestate"]
[045:077] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[045:078] 0x7fab6977e360: C->F: ["getdevicestate"]
[045:090] 0x7fab6977e360: C->F: ["comment","BC Other StatEvent: 6"]
[045:092] 0x7fab6977e360: C->F: ["comment","BC Other StatEvent: 12"]
[045:176] 0x7fab6977e360: F->C: ["getdevicestate","15","1",["__default_device","Plantronics .Audio 655 DSP Analog Stereo"],"2",["__default_device","Built-in Audio Digital Stereo (HDMI)","Plantronics .Audio 655 DSP Analog Stereo"],"0",["Integrated Camera"]]
[045:368] 0x7fab6977e360: C->F: ["setdevicestate",3,1,2,0,false]
[045:369] 0x7fab6977e360: C->F: ["getdevicestate"]
[045:371] 0x7fab6977e360: F->C: ["getdevicestate","15","1",["__default_device","Plantronics .Audio 655 DSP Analog Stereo"],"2",["__default_device","Built-in Audio Digital Stereo (HDMI)","Plantronics .Audio 655 DSP Analog Stereo"],"0",["Integrated Camera"]]
[045:377] 0x7fab6977e360: F->C: ["streamready","jid","preview","o1d2638-2",34,null,1280,720,1280,720,1,1]
[045:383] 0x7fab6977e360: C->F: ["comment","BC state change: 2 to 3. Error? 0"]
[045:392] 0x7fab6977e360: C->F: ["comment","BC state change: 3 to 4. Error? 0"]
[045:483] 0x7fab6977e360: F->C: ["getdevicestate","15","1",["__default_device","Plantronics .Audio 655 DSP Analog Stereo"],"2",["__default_device","Built-in Audio Digital Stereo (HDMI)","Plantronics .Audio 655 DSP Analog Stereo"],"0",["Integrated Camera"]]
[045:623] 0x7fab6977e360: C->F: ["jf",[["stun.l.google.com","19302"],["alt2.stun.l.google.com","19302"],["alt1.stun.l.google.com","19302"],["alt4.stun.l.google.com","19302"],["alt3.stun.l.google.com","19302"]],["CAESGwoSZ2FiYmVsbG9AZ21haWwuY29tEKrHj7TNKBoQ0iVjn+WvOLY4VIQNVcvpYQ==",["relay.google.com","19305","19305","443"]]]
[045:623] 0x7fab6977e360: C->F: ["jf",[["stun.l.google.com","19302"],["alt2.stun.l.google.com","19302"],["alt1.stun.l.google.com","19302"],["alt4.stun.l.google.com","19302"],["alt3.stun.l.google.com","19302"]],["CAESGwoSZ2FiYmVsbG9AZ21haWwuY29tEKzHj7TNKBoQ6QCo8d8a0RMHFDj7SXdYKQ==",["relay.google.com","19305","19305","443"]]]
[045:624] 0x7fab6977e360: C->F: ["jf",[["stun.l.google.com","19302"],["alt2.stun.l.google.com","19302"],["alt1.stun.l.google.com","19302"],["alt4.stun.l.google.com","19302"],["alt3.stun.l.google.com","19302"]],["CAESGwoSZ2FiYmVsbG9AZ21haWwuY29tEK3Hj7TNKBoQURsF56nbxzkBtmv6t3iDMQ==",["relay.google.com","19305","19305","443"]]]
[045:983] 0x7fab6977e360: C->F: ["jn","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063","v","s"]
[045:997] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"send initiate","time":113504}]]
[046:198] 0x7fab6977e510: F->C: ["fs",{"callId":"c1492350838998505063","callType":"v","pr":"a"}]
[046:203] 0x7fab6977e5a0: F->C: ["fs",{"callId":"c1492350838998505063","callType":"v","pr":"a"}]
[046:204] 0x7fab6977e360: F->C: ["jmistart","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063","Tue Mar 18 10:34:12 2014","v"]
[046:205] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jmistart"]
[046:205] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"allWritable":false,"anyRelay":false,"anyTcp":false,"anyWritable":false,"smoothedBWRecv":100000000,"smoothedBWSend":100000000}]
[046:206] 0x7fab6977e360: F->C: ["fs",{"callId":"c1492350838998505063","callType":"v","pr":"a"}]
[046:206] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[046:207] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[046:317] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:320] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP REQ (33751) [attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33751&AID=37&zx=vvpogtnyos2q&t=1\ncount=redacted&ofs=redacted&req0_t=redacted&req0_p=redacted&req0_c=redacted&req0__sc=redacted&req1_t=redacted&req1_p=redacted&req1_c=redacted&req1__sc=redacted&req2_t=redacted&req2_p=redacted&req2_c=redacted&req2__sc=redacted&req3_t=redacted&req3_p=redacted&req3_c=redacted&req3__sc=redacted&req4_t=redacted&req4_p=redacted&req4_c=redacted&req4__sc=redacted&req5_t=redacted&req5_p=redacted&req5_c=redacted&req5__sc=redacted&req6_t=redacted&req6_p=redacted&req6_c=redacted&req6__sc=redacted&req7_m=redacted&req7_c=redacted&req7__sc=redacted&req8_t=redacted&req8_p=redacted&req8_c=redacted&req8__sc=redacted&req9_t=redacted&req9_p=redacted&req9_c=redacted&req9__sc=redacted&req10_t=redacted&req10_p=redacted&req10_c=redacted&req10__sc=redacted&req11_t=redacted&req11_p=redacted&req11_c=redacted&req11__sc=redacted&req12_m=redacted&req12_c=redacted&req12__sc=redacted&req13_t=redacted&req13_p=redacted&req13_c=redacted&req13__sc=redacted&req14_t=redacted&req14_p=redacted&req14_c=redacted&req14__sc=redacted&req15_t=redacted&req15_p=redacted&req15_c=redacted&req15__sc=redacted&req16_m=redacted&req16_c=redacted&req16__sc=redacted&req17_t=redacted&req17_p=redacted&req17_c=redacted&req17__sc=redacted&req18_t=redacted&req18_p=redacted&req18_c=redacted&req18__sc=redacted&"]
[046:321] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ finished, sent request"]
[046:403] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33751) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33751&AID=37&zx=vvpogtnyos2q&t=1\n3 200"]
[046:406] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP TEXT (33751): [1,37,0]"]
[046:409] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33751) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33751&AID=37&zx=vvpogtnyos2q&t=1\n4 200"]
[046:410] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[046:416] 0x7fab6977e360: C->F: ["jlrtp","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"codecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"},"streams":[{"name":"main audio","ssrcs":[1010945861]}],"rtp-hdrext":[{"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level","id":1}]},"v":{"codecs":[[100,"VP8",1280,800,30],[116,"red",1280,800,30],[117,"ulpfec",1280,800,30],[99,"H264-SVC",1280,800,30],[97,"H264",1280,800,30],[98,"H263",1280,800,30]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"},"streams":[{"name":"main video","ssrcs":[4241607932,3539814471,1666844866],"ssrcGroups":[{"semantics":"SIM","ssrcs":[4241607932,3539814471,1666844866]}]}],"rtp-hdrext":[{"uri":"urn:ietf:params:rtp-hdrext:toffset","id":2},{"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time","id":3}]},"d":{"codecs":[[101,"google-data"]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"},"streams":[{"name":"","ssrcs":[3589165039]}]}}]
[046:417] 0x7fab6977e360: C->F: ["jtr","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063","i"]
[046:429] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:429] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ returned: nothing to send"]
[046:507] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv local description","time":113936}]]
[046:514] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"send candidate local","time":113944}]]
[046:523] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["10.0.3.228","51781","rtp","lZOLNITCPIy6LQ9k","AW/Rph8zwEFqILkrFVCfIEE3","0.99","udp","0","local","eth0"]]]
[046:529] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:531] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["10.0.3.228","51474","rtcp","lZOLNITCPIy6LQ9l","AW/Rph8zwEFqILkrFVCfIEE3","0.99","udp","0","local","eth0"]]]
[046:540] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:542] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["10.0.3.228","55794","data_rtp","NljvrzGha9Ncc1ON","xzznzeSk8HyqDpWwQcrjCWiD","0.99","udp","0","local","eth0"]]]
[046:562] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:563] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["10.0.3.228","52744","video_rtp","jLukK8KqRZJ5I9YJ","4npJpr2cr199RbjZIiRjnFih","0.99","udp","0","local","eth0"],["10.0.3.228","48670","video_rtcp","jLukK8KqRZJ5I9YK","4npJpr2cr199RbjZIiRjnFih","0.99","udp","0","local","eth0"]]]
[046:564] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:565] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"send candidate stun","time":114015}]]
[046:565] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["85.9.7.222","60664","rtp","lZOLNITCPIy6LQ9k","AW/Rph8zwEFqILkrFVCfIEE3","0.86","udp","0","stun","eth0"],["85.9.7.222","41551","rtcp","lZOLNITCPIy6LQ9l","AW/Rph8zwEFqILkrFVCfIEE3","0.86","udp","0","stun","eth0"]]]
[046:565] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:566] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["85.9.7.222","53067","video_rtp","jLukK8KqRZJ5I9YJ","4npJpr2cr199RbjZIiRjnFih","0.86","udp","0","stun","eth0"],["85.9.7.222","50475","video_rtcp","jLukK8KqRZJ5I9YK","4npJpr2cr199RbjZIiRjnFih","0.86","udp","0","stun","eth0"]]]
[046:566] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:567] 0x7fab6977e360: F->C: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["85.9.7.222","37144","data_rtp","NljvrzGha9Ncc1ON","xzznzeSk8HyqDpWwQcrjCWiD","0.86","udp","0","stun","eth0"]]]
[046:569] 0x7fab6977e360: C->F: ["comment","Relaying plugin message to WCS: jc"]
[046:570] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:573] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP REQ (33752) [attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33752&AID=44&zx=la8660qbqxua&t=1\ncount=redacted&ofs=redacted&req0_m=redacted&req0_c=redacted&req0__sc=redacted&req1_m=redacted&req1_c=redacted&req1__sc=redacted&req2_m=redacted&req2_c=redacted&req2__sc=redacted&req3_m=redacted&req3_c=redacted&req3__sc=redacted&req4_m=redacted&req4_c=redacted&req4__sc=redacted&req5_m=redacted&req5_c=redacted&req5__sc=redacted&req6_m=redacted&req6_c=redacted&req6__sc=redacted&"]
[046:573] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ finished, sent request"]
[046:743] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:743] 0x7fab6977e360: C->F: ["error","BC log msg, severe: startForwardChannel_ returned: connection already in progress"]
[046:757] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33752) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33752&AID=44&zx=la8660qbqxua&t=1\n3 200"]
[046:760] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP TEXT (33752): [1,48,1509]"]
[046:764] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33752) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33752&AID=44&zx=la8660qbqxua&t=1\n4 200"]
[046:764] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[046:806] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:808] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP REQ (33753) [attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33753&AID=55&zx=sm62iofzhois&t=1\ncount=redacted&ofs=redacted&req0_t=redacted&req0_p=redacted&req0_c=redacted&req0__sc=redacted&req1_t=redacted&req1_p=redacted&req1_c=redacted&req1__sc=redacted&req2_t=redacted&req2_p=redacted&req2_c=redacted&req2__sc=redacted&req3_t=redacted&req3_p=redacted&req3_c=redacted&req3__sc=redacted&"]
[046:808] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ finished, sent request"]
[046:935] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33753) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33753&AID=55&zx=sm62iofzhois&t=1\n3 200"]
[046:936] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP TEXT (33753): [1,55,0]"]
[046:938] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33753) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33753&AID=55&zx=sm62iofzhois&t=1\n4 200"]
[046:939] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[046:965] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[046:965] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ returned: nothing to send"]
[047:074] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":true}]
[047:147] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[047:149] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP REQ (33754) [attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33754&AID=57&zx=do97vmbfmlvc&t=1\ncount=redacted&ofs=redacted&req0_t=redacted&req0_p=redacted&req0_c=redacted&req0__sc=redacted&req1_t=redacted&req1_p=redacted&req1_c=redacted&req1__sc=redacted&req2_t=redacted&req2_p=redacted&req2_c=redacted&req2__sc=redacted&"]
[047:149] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ finished, sent request"]
[047:212] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33754) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33754&AID=57&zx=do97vmbfmlvc&t=1\n3 200"]
[047:212] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP TEXT (33754): [1,57,0]"]
[047:213] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33754) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33754&AID=57&zx=do97vmbfmlvc&t=1\n4 200"]
[047:214] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[047:217] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[047:222] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP REQ (33755) [attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33755&AID=57&zx=eh28atd9nkbu&t=1\ncount=redacted&ofs=redacted&req0_t=redacted&req0_p=redacted&req0_c=redacted&req0__sc=redacted&req1_t=redacted&req1_p=redacted&req1_c=redacted&req1__sc=redacted&"]
[047:223] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ finished, sent request"]
[047:357] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33755) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33755&AID=57&zx=eh28atd9nkbu&t=1\n3 200"]
[047:358] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP TEXT (33755): [1,58,207]"]
[047:363] 0x7fab6977e360: C->F: ["comment","BC log msg, info: XMLHTTP RESP (33755) [ attempt 1]: POST\nhttps://plus.google.com/hangouts/_/channel/bind?VER=8&clid=D5D73B7C32E0B888&gsessionid=7CM9Ynwl6n4&prop=hangout&ujidr=hangoutD87FC56B&eid&ec=%5B%22ci%3Aec%22%2C0%2C0%2C0%2C%22chat_wcs_20140310.133048_RC1%22%5D&SID=114986E0E372AAA1&RID=33755&AID=57&zx=eh28atd9nkbu&t=1\n4 200"]
[047:363] 0x7fab6977e360: C->F: ["comment","BC log msg, info: Request complete"]
[047:365] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_"]
[047:365] 0x7fab6977e360: C->F: ["comment","BC log msg, info: startForwardChannel_ returned: nothing to send"]
[047:632] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","data_rtp","6czfDzwsVb7B+kb5","Unts7t2t1zj5N5L/","3","udp","0","local","0"]]]
[047:634] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","video_rtp","zereukutna352YKQ","BkGLOegBs8zzpL+G","3","udp","0","local","0"]]]
[047:637] 0x7fab6977e360: C->F: ["jack","c1492350838998505063",1395138854106]
[047:641] 0x7fab6977e360: C->F: ["jrtp","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"codecs":[[103,"ISAC",1,32000,16000],[9,"G722",1,64000,16000],[105,"CN",1,0,16000],[0,"PCMU",1,0,8000],[13,"CN",1,0,8000],[111,"OPUS",2,0,48000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[106,"CN",1,0,32000]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"},"rtp-hdrext":[{"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level","id":1}]},"v":{"codecs":[[100,"VP8",640,360,30]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"},"rtp-hdrext":[{"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time","id":3}]},"d":{"codecs":[[101,"google-data"]],"rtcp_mux":true,"crypto":{"cs":"AES_CM_128_HMAC_SHA1_80","kp":"REDACTED","tag":"1"}}}]
[047:642] 0x7fab6977e360: C->F: ["comment","jrtp: Converting to jp: [\"jrtp\",\"muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com\",\"c1492350838998505063\",{\"a\":{\"codecs\":[[103,\"ISAC\",1,32000,16000],[9,\"G722\",1,64000,16000],[105,\"CN\",1,0,16000],[0,\"PCMU\",1,0,8000],[13,\"CN\",1,0,8000],[111,\"OPUS\",2,0,48000],[109,\"CELT\",1,64000,32000],[110,\"CELT\",2,64000,32000],[106,\"CN\",1,0,32000]],\"rtcp_mux\":true,\"crypto\":{\"cs\":\"AES_CM_128_HMAC_SHA1_80\",\"kp\":\"inline:gTmNiXaURiEJ9FwJ29BqZnSNHQ0Q3PgwEbIiwAD7\",\"tag\":\"1\"},\"rtp-hdrext\":[{\"uri\":\"urn:ietf:params:rtp-hdrext:ssrc-audio-level\",\"id\":1}]},\"v\":{\"codecs\":[[100,\"VP8\",640,360,30]],\"rtcp_mux\":true,\"crypto\":{\"cs\":\"AES_CM_128_HMAC_SHA1_80\",\"kp\":\"inline:hbrBsbxgaFIKmw5J2MsxysKTHE4vDUQ9dkkZojZO\",\"tag\":\"1\"},\"rtp-hdrext\":[{\"uri\":\"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time\",\"id\":3}]},\"d\":{\"codecs\":[[101,\"google-data\"]],\"rtcp_mux\":true,\"crypto\":{\"cs\":\"AES_CM_128_HMAC_SHA1_80\",\"kp\":\"inline:PyvKKd79ANBh58wyU9JkHiz64Pf/rGHl8eV572VD\",\"tag\":\"1\"}}}]"]
[047:643] 0x7fab6977e360: C->F: ["comment","jrtp: Conversion Results: []"]
[047:644] 0x7fab6977e360: C->F: ["comment","MultiwayWcsFailover - Started monitoring meeting. JID: muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com/hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80"]
[047:645] 0x7fab6977e360: C->F: ["comment","MultiwayWcsFailover - multiwaywcsfailover source changed to CONNECTIVITY"]
[047:648] 0x7fab6977e360: C->F: ["comment","JS callInfo: muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84_groupchat_google_com/nn/video;urlStart=true,allowed=true,retries=0;restarted=false,autoRestarted=false,camMute=false,micMute=false"]
[047:654] 0x7fab6977e360: C->F: ["ja","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063"]
[047:655] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","data_rtp","6czfDzwsVb7B+kb5","Unts7t2t1zj5N5L/","2","tcp","0","local","0"]]]
[047:656] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","443","data_rtp","6czfDzwsVb7B+kb5","Unts7t2t1zj5N5L/","1","ssltcp","0","local","0"]]]
[047:656] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","video_rtp","zereukutna352YKQ","BkGLOegBs8zzpL+G","2","tcp","0","local","0"]]]
[047:657] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","443","video_rtp","zereukutna352YKQ","BkGLOegBs8zzpL+G","1","ssltcp","0","local","0"]]]
[047:657] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","rtp","Q4UDI/NdZ1gmmeRB","/g+ClWvJDEuOthmc","3","udp","0","local","0"]]]
[047:672] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv candidate local","time":115153}]]
[047:679] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv remote description","time":115192}]]
[047:728] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","19305","rtp","Q4UDI/NdZ1gmmeRB","/g+ClWvJDEuOthmc","2","tcp","0","local","0"]]]
[047:731] 0x7fab6977e360: C->F: ["jc","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[["173.194.70.127","443","rtp","Q4UDI/NdZ1gmmeRB","/g+ClWvJDEuOthmc","1","ssltcp","0","local","0"]]]
[047:771] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"transport writable","time":115222}]]
[047:773] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"allWritable":false,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000}]
[047:774] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000}]
[047:870] 0x7fab6977e360: C->F: ["comment","Stream Requests for up streams received from WCS: {participantId: function $QC(a){C(this,a,\"guc:ac\",-1,[])}, sourceId: 4241607932, mediaType: kb, resolution: [object Object], frameRate: 30}"]
[047:872] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv first video packet","time":115366}]]
[047:879] 0x7fab6977e360: C->F: ["jrtp","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"streams":[{"nick":"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80","name":"main audio","ssrcs":[1010945861],"participantName":"Gabi Pavel"}],"partial":true},"v":{"streams":[{"nick":"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80","name":"main video","ssrcs":[2844740679],"participantName":"Gabi Pavel"}],"partial":true},"d":{"streams":[{"nick":"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80","name":"","ssrcs":[3589165039],"participantName":"Gabi Pavel"}],"partial":true}}]
[047:880] 0x7fab6977e360: C->F: ["comment","jrtp: Converting to jp: [\"jrtp\",\"muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com\",\"c1492350838998505063\",{\"a\":{\"streams\":[{\"nick\":\"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80\",\"name\":\"main audio\",\"ssrcs\":[1010945861],\"participantName\":\"Gabi Pavel\"}],\"partial\":true},\"v\":{\"streams\":[{\"nick\":\"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80\",\"name\":\"main video\",\"ssrcs\":[2844740679],\"participantName\":\"Gabi Pavel\"}],\"partial\":true},\"d\":{\"streams\":[{\"nick\":\"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80\",\"name\":\"\",\"ssrcs\":[3589165039],\"participantName\":\"Gabi Pavel\"}],\"partial\":true}}]"]
[047:881] 0x7fab6977e360: C->F: ["comment","jrtp: Conversion Results: [[\"jp\",\"muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com\",\"c1492350838998505063\",\"hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80\",[{\"type\":\"a\",\"s\":\"1010945861\"},{\"type\":\"v\",\"s\":\"2844740679\"}]]]"]
[047:882] 0x7fab6977e360: C->F: ["comment","Received jingle notify, nick: hangoutD87FC56B_ephemeral.id.google.com^b2a74f9257ea80, audioSsrc: 1010945861, videoSsrc: 2844740679, isActive: true, isLocal: true"]
[047:884] 0x7fab6977e360: C->F: ["setcalloptions","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"video_process_adaptation_threshhold":0.1,"video_system_low_adaptation":0.75,"video_system_high_adaptation":0.9}]
[047:886] 0x7fab6977e360: C->F: ["scalevolume","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,1,"1010945861"]
[047:892] 0x7fab6977e360: C->F: ["mediaeffects","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"id":"meta_effect","dir":"tx","action":"init","effect_handle":"boost_10","video_index":4,"voice_ssrc":1010945861,"video_ssrc":"2844740679"}]
[047:893] 0x7fab6977e360: C->F: ["mediaeffects","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"id":"meta_effect","dir":"tx","action":"enable","effect_handle":"boost_10","properties":{"clear":false,"remove":[],"init":[{"effect_handle":"11","id":"temporal_blur","properties":{"learning_rate":0.9}},{"effect_handle":"12","id":"auto_bcs","properties":{"target_brightness":90,"max_auto_brightness":0.6,"min_auto_brightness":-0.2,"constrast":0.6,"saturation":0.1}},{"effect_handle":"13","id":"surface_blur","properties":{"window_size":7,"edge_min_threshold":10,"edge_max_threshold":80}}],"pipeline":[{"effect_handle":"11","id":"temporal_blur","properties":{"learning_rate":0.9}},{"effect_handle":"12","id":"auto_bcs","properties":{"target_brightness":90,"max_auto_brightness":0.6,"min_auto_brightness":-0.2,"constrast":0.6,"saturation":0.1}},{"effect_handle":"13","id":"surface_blur","properties":{"window_size":7,"edge_min_threshold":10,"edge_max_threshold":80}}],"get_effect_descriptions":false},"video_index":4,"voice_ssrc":1010945861,"video_ssrc":"2844740679"}]
[047:896] 0x7fab6977e360: C->F: ["jv","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"v":[{"type":"static","ssrc":4241607932,"width":1280,"height":720,"framerate":30}]}]
[047:896] 0x7fab6977e360: C->F: ["comment","Stream Requests for up streams sent to plugin: jv,muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com,c1492350838998505063,[object Object]"]
[047:909] 0x7fab6977e360: F->C: ["effect-notify","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"effect_handle":"boost_10","status":"initialized"}]
[047:917] 0x7fab6977e360: F->C: ["effect-notify","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"effect_handle":"boost_10","meta_effect_notify":{"initialized":[{"effect_handle":"11","enabled":false,"id":"temporal_blur"},{"effect_handle":"12","enabled":false,"id":"auto_bcs"},{"effect_handle":"13","enabled":false,"id":"surface_blur"}],"pipeline":[{"effect_handle":"11","enabled":true,"id":"temporal_blur"},{"effect_handle":"12","enabled":true,"id":"auto_bcs"},{"effect_handle":"13","enabled":true,"id":"surface_blur"}]}}]
[047:924] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv view request","time":115416}]]
[048:609] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[048:672] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[048:709] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[049:173] 0x7fab6977e360: HandleOnlineCheck: Starting check
[049:174] 0x7fab6977e360: HandleOnlineCheck: OK; current state: 3
[049:674] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[050:675] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[050:996] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":325},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000,"v":{"rtt":557}}]
[052:178] 0x7fab6977e360: F->C: ["latency-events","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",[{"key":"recv first audio packet","time":119650}]]
[055:002] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":57},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000,"v":{"rtt":67}}]
[055:683] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",10,[[{"b":22412,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":226,"erl":-100,"erle":-100,"fl":0,"j":1,"p":229,"pl":0,"rtt":-1,"s":1010945861,"sn":25378,"t":"s"}],[{"ar":0,"b":193674,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":30,"h":720,"nack":-1,"nbr":364148,"p":377,"pbr":700,"pc":-1,"pl":0,"rtt":40,"s":4241607932,"sfps":30,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":359318,"arbw":0,"asbw":323280,"lbd":0,"rtxbr":0,"t":"b","tbr":323280,"txbr":393366}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":46,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":57,"sb":29466,"sbs":4373}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":1874,"rbs":274,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":49,"sb":242025,"sbs":47779}]],{"cpu":150,"cpus":4,"tcpu":259,"v":2}]
[055:688] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[055:690] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[055:692] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[058:007] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":31},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000,"v":{"rtt":34}}]
[058:987] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[059:087] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[061:013] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":100000000,"smoothedBWSend":100000000,"v":{"rtt":29}}]
[061:751] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",true]
[061:753] 0x7fab6977e360: C->F: ["streamoff","jid","preview","o1d2638-2",34]
[062:094] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":328745,"v":{"rtt":28}}]
[065:597] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",20,[[{"b":55602,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":227,"erl":-100,"erle":-100,"fl":0,"j":1,"p":560,"pl":0,"rtt":-1,"s":1010945861,"sn":25708,"t":"s"}],[{"ar":0,"b":374365,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":848,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":152944}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":138,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":72700,"sbs":4303}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":4614,"rbs":234,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":620176,"sbs":20475}]],{"cpu":136,"cpus":4,"tcpu":221,"v":2}]
[065:606] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 5"]
[065:611] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 5"]
[065:615] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[066:298] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[066:398] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[069:401] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[069:501] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[071:103] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":361619,"v":{"rtt":28}}]
[071:203] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[071:303] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[072:805] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[072:905] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[074:406] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[074:507] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[075:608] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",30,[[{"b":88234,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":608,"erl":-100,"erle":-100,"fl":0,"j":1,"p":886,"pl":0,"rtt":-1,"s":1010945861,"sn":26037,"t":"s"}],[{"ar":0,"b":375261,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":852,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":230,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":115296,"sbs":4315}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":7328,"rbs":232,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":624560,"sbs":204}]],{"cpu":28,"cpus":4,"tcpu":62,"v":2}]
[075:613] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[075:618] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[075:622] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[078:711] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[078:811] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[082:415] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[082:515] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[085:619] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",40,[[{"b":121084,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":826,"erl":-100,"erle":-100,"fl":0,"j":0,"p":1213,"pl":0,"rtt":-1,"s":1010945861,"sn":26362,"t":"s"}],[{"ar":0,"b":375261,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":852,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":322,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":158118,"sbs":4240}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":9680,"rbs":270,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":626586,"sbs":226}]],{"cpu":30,"cpus":4,"tcpu":57,"v":2}]
[085:624] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[085:630] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[085:634] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[089:623] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[089:723] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[090:524] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[090:624] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[091:650] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[092:651] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[095:630] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",50,[[{"b":154714,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":421,"erl":-100,"erle":-100,"fl":0,"j":1,"p":1542,"pl":0,"rtt":-1,"s":1010945861,"sn":26692,"t":"s"}],[{"ar":0,"b":375261,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":852,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":414,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":201754,"sbs":4042}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":11894,"rbs":234,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":628516,"sbs":209}]],{"cpu":30,"cpus":4,"tcpu":64,"v":2}]
[095:634] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[095:640] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[095:644] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[099:134] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[099:234] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[102:137] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[102:237] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[103:638] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[103:738] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[104:079] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":397780,"v":{"rtt":28}}]
[105:640] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",60,[[{"b":186766,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":845,"erl":-100,"erle":-100,"fl":0,"j":0,"p":1865,"pl":0,"rtt":-1,"s":1010945861,"sn":27015,"t":"s"}],[{"ar":0,"b":375261,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":852,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":506,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":243540,"sbs":4026}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":14062,"rbs":232,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":630478,"sbs":210}]],{"cpu":30,"cpus":4,"tcpu":61,"v":2}]
[105:645] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[105:651] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[105:655] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[107:242] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[107:342] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[108:043] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[108:143] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[112:547] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[112:647] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[113:048] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[113:248] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[113:348] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",2,[0,[]],5]
[113:448] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[114:449] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[114:549] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[115:651] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",70,[[{"b":220520,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":1974,"erl":-100,"erle":-100,"fl":0,"j":0,"p":2197,"pl":0,"rtt":-1,"s":1010945861,"sn":27344,"t":"s"}],[{"ar":0,"b":375261,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":852,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":422724,"lbd":0,"rtxbr":0,"t":"b","tbr":422724,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":598,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":287670,"sbs":4512}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":16138,"rbs":224,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":632700,"sbs":216}]],{"cpu":30,"cpus":4,"tcpu":56,"v":2}]
[115:656] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 13"]
[115:661] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 13"]
[115:665] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[116:051] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[116:251] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[116:752] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[116:852] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[117:853] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[117:953] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[118:654] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[118:754] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[119:655] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[119:755] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[122:161] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",false]
[122:167] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[122:216] 0x7fab6977e360: C->F: ["streamon","jid","preview","o1d2823-1",42,null,1280,720]
[122:222] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":true}]
[122:758] 0x7fab6977e360: F->C: ["streamready","jid","preview","o1d2823-1",42,null,1280,720,1280,720,1,1]
[125:563] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",80,[[{"b":252339,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":327,"erl":-100,"erle":-100,"fl":0,"j":1,"p":2519,"pl":0,"rtt":-1,"s":1010945861,"sn":27665,"t":"s"}],[{"ar":0,"b":426692,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":30,"h":720,"nack":-1,"nbr":103529,"p":948,"pbr":700,"pc":-1,"pl":0,"rtt":40,"s":4241607932,"sfps":25,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":93418,"arbw":0,"asbw":457542,"lbd":0,"rtxbr":0,"t":"b","tbr":457542,"txbr":204086}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":690,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":329142,"sbs":4258}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":18586,"rbs":267,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":770003,"sbs":34976}]],{"cpu":54,"cpus":4,"tcpu":117,"v":2}]
[125:567] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[125:569] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[125:571] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[127:665] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[127:765] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[128:266] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[128:366] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[129:267] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[129:367] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[129:667] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[130:168] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[130:268] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[130:368] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[130:468] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[130:668] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[131:671] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[132:672] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[132:772] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[133:674] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[134:676] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[135:577] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",90,[[{"b":285315,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":464,"erl":-100,"erle":-100,"fl":0,"j":1,"p":2848,"pl":0,"rtt":-1,"s":1010945861,"sn":27995,"t":"s"}],[{"ar":0,"b":621684,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":30,"h":720,"nack":-1,"nbr":453094,"p":1312,"pbr":700,"pc":-1,"pl":0,"rtt":40,"s":4241607932,"sfps":30,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":443116,"arbw":0,"asbw":430342,"lbd":0,"rtxbr":0,"t":"b","tbr":430342,"txbr":443116}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":782,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":372293,"sbs":4321}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":21320,"rbs":264,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1394129,"sbs":58309}]],{"cpu":176,"cpus":4,"tcpu":262,"v":2}]
[135:586] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 7"]
[135:590] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 7"]
[135:592] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[136:078] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",2,[0,[]],5]
[136:178] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[139:684] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[139:884] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[140:785] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[140:985] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[141:588] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[141:688] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[141:892] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",true]
[141:895] 0x7fab6977e360: C->F: ["streamoff","jid","preview","o1d2823-1",42]
[142:789] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[142:889] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[143:438] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",false]
[143:444] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[143:458] 0x7fab6977e360: C->F: ["streamon","jid","preview","o1d2823-2",91,null,1280,720]
[143:474] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":true}]
[143:991] 0x7fab6977e360: F->C: ["streamready","jid","preview","o1d2823-2",91,null,1280,720,1280,720,1,1]
[145:593] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",100,[[{"b":318848,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":252,"erl":-100,"erle":-100,"fl":0,"j":1,"p":3177,"pl":0,"rtt":-1,"s":1010945861,"sn":28324,"t":"s"}],[{"ar":0,"b":778119,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":28,"h":720,"nack":-1,"nbr":355170,"p":1593,"pbr":700,"pc":-1,"pl":0,"rtt":43,"s":4241607932,"sfps":1,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":56185,"arbw":0,"asbw":33400,"lbd":0,"rtxbr":0,"t":"b","tbr":33400,"txbr":56185}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":874,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":415880,"sbs":4161}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":24294,"rbs":339,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1827025,"sbs":14450}]],{"cpu":156,"cpus":4,"tcpu":250,"v":2}]
[145:597] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 8"]
[145:600] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 8"]
[145:602] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[145:925] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",true]
[145:930] 0x7fab6977e360: C->F: ["streamoff","jid","preview","o1d2823-2",91]
[146:794] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[146:894] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[147:044] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",false]
[147:048] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":false}]
[147:061] 0x7fab6977e360: C->F: ["streamon","jid","preview","o1d2823-3",74,null,1280,720]
[147:074] 0x7fab6977e360: C->F: ["jec",[[96,"H264-SVC",1280,720,30]],{"num_threads":-1,"cpu_profile":61,"apply_immediately":true,"force_reopen":true}]
[147:795] 0x7fab6977e360: F->C: ["streamready","jid","preview","o1d2823-3",74,null,1280,720,1280,720,1,1]
[148:195] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":394783,"v":{"rtt":28}}]
[149:197] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":388238,"v":{"rtt":28}}]
[149:727] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[149:827] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[150:199] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":381693,"v":{"rtt":28}}]
[150:693] 0x7fab6977e360: C->F: ["vmute","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",true]
[150:696] 0x7fab6977e360: C->F: ["streamoff","jid","preview","o1d2823-3",74]
[151:200] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":375147,"v":{"rtt":28}}]
[152:201] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":368602,"v":{"rtt":28}}]
[153:202] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":362056,"v":{"rtt":28}}]
[154:203] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":355568,"v":{"rtt":28}}]
[154:703] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[155:204] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":349140,"v":{"rtt":28}}]
[155:633] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",110,[[{"b":350667,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":444,"erl":-100,"erle":-100,"fl":0,"j":1,"p":3500,"pl":0,"rtt":-1,"s":1010945861,"sn":28648,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":40,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":37072,"lbd":0,"rtxbr":0,"t":"b","tbr":37072,"txbr":17272}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":966,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":457411,"sbs":4235}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":26854,"rbs":268,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1865297,"sbs":2992}]],{"cpu":76,"cpus":4,"tcpu":132,"v":2}]
[155:639] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 5"]
[155:644] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 5"]
[155:649] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[155:657] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[156:159] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":342713,"v":{"rtt":28}}]
[157:160] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":336351,"v":{"rtt":28}}]
[158:161] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":329990,"v":{"rtt":28}}]
[159:162] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":323660,"v":{"rtt":28}}]
[159:662] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[160:163] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":317331,"v":{"rtt":28}}]
[160:663] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[161:164] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":311001,"v":{"rtt":28}}]
[161:664] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[162:165] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":304672,"v":{"rtt":28}}]
[162:240] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[162:440] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[163:166] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":298342,"v":{"rtt":28}}]
[163:241] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[163:341] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[164:167] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":292013,"v":{"rtt":28}}]
[165:168] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":285683,"v":{"rtt":28}}]
[165:644] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",120,[[{"b":382524,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":241,"erl":-100,"erle":-100,"fl":0,"j":0,"p":3818,"pl":0,"rtt":-1,"s":1010945861,"sn":28964,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1058,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":499154,"sbs":4543}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":29172,"rbs":155,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1867329,"sbs":186}]],{"cpu":30,"cpus":4,"tcpu":61,"v":2}]
[165:650] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[165:657] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[165:662] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[165:669] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[166:171] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":279354,"v":{"rtt":28}}]
[166:672] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[167:172] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":273024,"v":{"rtt":28}}]
[168:173] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":266695,"v":{"rtt":28}}]
[169:147] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[169:150] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":260365,"v":{"rtt":28}}]
[169:247] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[170:175] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":254036,"v":{"rtt":28}}]
[170:949] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[171:049] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[171:176] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":247706,"v":{"rtt":28}}]
[172:150] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":241377,"v":{"rtt":28}}]
[173:151] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":235047,"v":{"rtt":28}}]
[174:152] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":228718,"v":{"rtt":28}}]
[175:153] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":222388,"v":{"rtt":28}}]
[175:653] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",130,[[{"b":413293,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":847,"erl":-100,"erle":-100,"fl":0,"j":0,"p":4135,"pl":0,"rtt":-1,"s":1010945861,"sn":29290,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1150,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":539477,"sbs":3487}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":31248,"rbs":221,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1869281,"sbs":119}]],{"cpu":30,"cpus":4,"tcpu":53,"v":2}]
[175:660] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 23"]
[175:667] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 23"]
[175:675] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[176:154] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":216059,"v":{"rtt":28}}]
[177:155] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":209729,"v":{"rtt":28}}]
[177:756] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[177:827] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[178:156] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":203400,"v":{"rtt":28}}]
[179:157] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":197071,"v":{"rtt":28}}]
[180:030] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[180:158] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":190741,"v":{"rtt":28}}]
[180:230] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[181:159] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":184412,"v":{"rtt":28}}]
[182:160] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":178082,"v":{"rtt":28}}]
[183:161] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":171753,"v":{"rtt":28}}]
[183:533] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[183:633] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[184:162] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":164843,"v":{"rtt":28}}]
[185:163] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":157933,"v":{"rtt":28}}]
[185:564] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",140,[[{"b":442813,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":339,"erl":-100,"erle":-100,"fl":0,"j":0,"p":4445,"pl":0,"rtt":-1,"s":1010945861,"sn":29596,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1242,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":578643,"sbs":3917}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":33508,"rbs":202,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1871447,"sbs":249}]],{"cpu":30,"cpus":4,"tcpu":56,"v":2}]
[185:569] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 18"]
[185:576] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 18"]
[185:582] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[186:164] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":150397,"v":{"rtt":28}}]
[187:165] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":142183,"v":{"rtt":28}}]
[187:337] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[187:437] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[187:537] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[187:637] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[188:166] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":133239,"v":{"rtt":28}}]
[189:168] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":124294,"v":{"rtt":28}}]
[190:169] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":116486,"v":{"rtt":28}}]
[191:170] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":110030,"v":{"rtt":28}}]
[192:171] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":103573,"v":{"rtt":28}}]
[193:172] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":97117,"v":{"rtt":28}}]
[194:144] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[194:173] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":90660,"v":{"rtt":28}}]
[194:244] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[195:174] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":84204,"v":{"rtt":28}}]
[195:546] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",150,[[{"b":475975,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":923,"erl":-100,"erle":-100,"fl":0,"j":1,"p":4771,"pl":0,"rtt":-1,"s":1010945861,"sn":29920,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1334,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":621622,"sbs":4286}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":35722,"rbs":234,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1873485,"sbs":207}]],{"cpu":27,"cpus":4,"tcpu":81,"v":2}]
[195:552] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 15"]
[195:556] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 15"]
[195:559] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[196:175] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":77747,"v":{"rtt":28}}]
[197:176] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":71291,"v":{"rtt":28}}]
[197:948] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[198:148] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[198:177] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":64834,"v":{"rtt":28}}]
[199:178] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":58378,"v":{"rtt":28}}]
[200:179] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":51922,"v":{"rtt":28}}]
[201:180] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":44966,"v":{"rtt":28}}]
[202:052] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[202:152] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[202:154] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":40637,"v":{"rtt":28}}]
[204:254] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[204:355] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[205:556] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",160,[[{"b":506865,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":278,"erl":-100,"erle":-100,"fl":0,"j":0,"p":5085,"pl":0,"rtt":-1,"s":1010945861,"sn":30235,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1426,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":662220,"sbs":3883}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":37890,"rbs":191,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1875263,"sbs":106}]],{"cpu":26,"cpus":4,"tcpu":88,"v":2}]
[205:558] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 10"]
[205:560] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 10"]
[205:562] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[215:566] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",170,[[{"b":538068,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":138,"erl":-100,"erle":-100,"fl":0,"j":0,"p":5401,"pl":0,"rtt":-1,"s":1010945861,"sn":30551,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1518,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":703222,"sbs":3863}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":40150,"rbs":250,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1877365,"sbs":199}]],{"cpu":29,"cpus":4,"tcpu":67,"v":2}]
[215:573] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 4"]
[215:576] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 4"]
[215:577] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[216:768] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[216:868] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[225:577] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",180,[[{"b":568878,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":311,"erl":-100,"erle":-100,"fl":0,"j":1,"p":5715,"pl":0,"rtt":-1,"s":1010945861,"sn":30863,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1610,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":743498,"sbs":4268}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":42226,"rbs":155,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1879565,"sbs":268}]],{"cpu":29,"cpus":4,"tcpu":75,"v":2}]
[225:583] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 7"]
[225:590] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 7"]
[225:598] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[226:178] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[226:278] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[228:380] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[228:480] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[235:619] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",190,[[{"b":599718,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":248,"erl":-100,"erle":-100,"fl":0,"j":1,"p":6032,"pl":0,"rtt":-1,"s":1010945861,"sn":31186,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1702,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":784113,"sbs":4043}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":44440,"rbs":250,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1881425,"sbs":185}]],{"cpu":28,"cpus":4,"tcpu":83,"v":2}]
[235:625] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 18"]
[235:632] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 18"]
[235:638] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[245:629] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",200,[[{"b":631857,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":423,"erl":-100,"erle":-100,"fl":0,"j":1,"p":6350,"pl":0,"rtt":-1,"s":1010945861,"sn":31497,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1794,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":825880,"sbs":4405}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":46654,"rbs":187,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1883295,"sbs":195}]],{"cpu":29,"cpus":4,"tcpu":78,"v":2}]
[245:636] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 15"]
[245:643] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 15"]
[245:648] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[248:659] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[249:660] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[251:635] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[251:736] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[255:640] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",210,[[{"b":664420,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":1521,"erl":-100,"erle":-100,"fl":0,"j":1,"p":6674,"pl":0,"rtt":-1,"s":1010945861,"sn":31822,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1886,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":868429,"sbs":3762}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":48914,"rbs":293,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1885187,"sbs":200}]],{"cpu":30,"cpus":4,"tcpu":61,"v":2}]
[255:645] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[255:650] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[255:655] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[265:651] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",220,[[{"b":695918,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":625,"erl":-100,"erle":-100,"fl":0,"j":0,"p":6993,"pl":0,"rtt":-1,"s":1010945861,"sn":32146,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":1978,"rbs":1,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":909674,"sbs":3888}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":51174,"rbs":203,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1887467,"sbs":180}]],{"cpu":29,"cpus":4,"tcpu":79,"v":2}]
[265:656] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[265:661] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[265:665] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[266:151] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[266:251] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[275:661] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",230,[[{"b":724944,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":1594,"erl":-100,"erle":-100,"fl":0,"j":1,"p":7290,"pl":0,"rtt":-1,"s":1010945861,"sn":32441,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2070,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":947818,"sbs":3965}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":53296,"rbs":215,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1889483,"sbs":200}]],{"cpu":29,"cpus":4,"tcpu":78,"v":2}]
[275:666] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[275:671] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[275:675] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[277:763] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[277:863] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[279:865] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[279:966] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[285:571] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",240,[[{"b":755512,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":235,"erl":-100,"erle":-100,"fl":0,"j":0,"p":7601,"pl":0,"rtt":-1,"s":1010945861,"sn":32747,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2162,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":987905,"sbs":3969}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":55602,"rbs":195,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1891623,"sbs":251}]],{"cpu":29,"cpus":4,"tcpu":70,"v":2}]
[285:576] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[285:581] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[285:584] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[287:173] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[287:273] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[287:373] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",2,[0,[]],5]
[287:473] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[289:475] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[289:575] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[290:977] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[291:177] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[293:179] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[293:279] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[295:581] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",250,[[{"b":788086,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":482,"erl":-100,"erle":-100,"fl":0,"j":0,"p":7923,"pl":0,"rtt":-1,"s":1010945861,"sn":33065,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2254,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1030357,"sbs":4565}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":57724,"rbs":230,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1893547,"sbs":165}]],{"cpu":30,"cpus":4,"tcpu":64,"v":2}]
[295:589] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 10"]
[295:595] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 10"]
[295:599] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[296:883] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[296:983] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[299:185] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[299:285] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[303:990] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[304:190] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[305:591] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",260,[[{"b":821214,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":510,"erl":-100,"erle":-100,"fl":0,"j":0,"p":8250,"pl":0,"rtt":-1,"s":1010945861,"sn":33391,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2346,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1073404,"sbs":4458}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":60030,"rbs":232,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1895617,"sbs":242}]],{"cpu":28,"cpus":4,"tcpu":79,"v":2}]
[305:597] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[305:605] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 12"]
[305:609] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[305:791] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[305:891] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[306:192] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[306:292] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[315:601] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",270,[[{"b":850855,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":134,"erl":-100,"erle":-100,"fl":0,"j":0,"p":8557,"pl":0,"rtt":-1,"s":1010945861,"sn":33704,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2438,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1112599,"sbs":3750}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":62156,"rbs":187,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1897665,"sbs":196}]],{"cpu":30,"cpus":4,"tcpu":52,"v":2}]
[315:607] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[315:611] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 14"]
[315:614] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[325:038] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[325:138] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[325:639] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",280,[[{"b":881439,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":747,"erl":-100,"erle":-100,"fl":0,"j":1,"p":8867,"pl":0,"rtt":-1,"s":1010945861,"sn":34015,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2530,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1152425,"sbs":4346}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":64324,"rbs":181,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1899627,"sbs":216}]],{"cpu":30,"cpus":4,"tcpu":56,"v":2}]
[325:642] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 9"]
[325:644] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 9"]
[325:644] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[333:852] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[333:952] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[335:654] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",290,[[{"b":911683,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":606,"erl":-100,"erle":-100,"fl":0,"j":1,"p":9173,"pl":0,"rtt":-1,"s":1010945861,"sn":34316,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2622,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1192248,"sbs":4251}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":66584,"rbs":219,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1901503,"sbs":212}]],{"cpu":27,"cpus":4,"tcpu":76,"v":2}]
[335:659] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 4"]
[335:664] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 4"]
[335:669] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[335:754] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[337:656] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[338:657] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[339:458] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[339:558] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[341:560] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[341:761] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[341:861] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[341:961] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[342:662] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[343:663] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[344:664] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[345:164] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[345:264] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[345:565] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",300,[[{"b":943511,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":2661,"erl":-100,"erle":-100,"fl":0,"j":0,"p":9487,"pl":0,"rtt":-1,"s":1010945861,"sn":34627,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2714,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1233510,"sbs":4431}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":68798,"rbs":281,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1903697,"sbs":213}]],{"cpu":30,"cpus":4,"tcpu":69,"v":2}]
[345:570] 0x7fab6977e360: C->F: ["comment","Debug participants for session c1492350838998505063:   nick = hangoutD87FC56B@ephemeral.id.google.com\n  audio SSRCs = 1010945861\n  video SSRCs = 2844740679\n  participant = Gabi Pavel"]
[345:572] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[345:578] 0x7fab6977e360: C->F: ["comment","Debug participants for session c1492350838998505063:   nick = hangoutD87FC56B@ephemeral.id.google.com\n  audio SSRCs = 1010945861\n  video SSRCs = 2844740679\n  participant = Gabi Pavel"]
[345:579] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 11"]
[345:583] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[345:665] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[346:666] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[347:367] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[347:467] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[348:668] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[349:669] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[349:671] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[349:769] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[350:270] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[350:370] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[350:670] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
[351:871] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[351:972] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[353:073] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[353:173] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[354:041] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":29},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":40637,"v":{"rtt":28}}]
[355:576] 0x7fab6977e360: F->C: ["jmidata","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",310,[[{"b":975075,"c":"ISAC","ecqmin":-1,"edm":-1,"eds":-1,"en":406,"erl":-100,"erle":-100,"fl":0,"j":0,"p":9809,"pl":0,"rtt":-1,"s":1010945861,"sn":34953,"t":"s"}],[{"ar":0,"b":809085,"c":"VP8","cd":-1,"cj":-1,"et":-1,"eu":-1,"fir":-1,"fl":0,"fps":0,"h":720,"nack":-1,"nbr":0,"p":1741,"pbr":700,"pc":-1,"pl":0,"rtt":39,"s":4241607932,"sfps":0,"sgs":null,"ss":[4241607932,3539814471,1666844866],"t":"s","w":1280},{"abr":0,"arbw":0,"asbw":42955,"lbd":0,"rtxbr":0,"t":"b","tbr":42955,"txbr":0}]],[[{"f":7,"lc":["rtp","local","udp","10.0.3.228:51781"],"rb":2806,"rbs":0,"rc":["rtp","local","udp","173.194.70.127:19305"],"rtt":29,"sb":1274951,"sbs":4122}],[{"f":7,"lc":["video_rtp","local","udp","10.0.3.228:52744"],"rb":71058,"rbs":249,"rc":["video_rtp","local","udp","173.194.70.127:19305"],"rtt":28,"sb":1905497,"sbs":200}]],{"cpu":30,"cpus":4,"tcpu":69,"v":2}]
[355:581] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 16"]
[355:587] 0x7fab6977e360: C->F: ["comment","Latest max plugin message processing time = 16"]
[355:591] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[356:677] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[356:777] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[356:977] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",1,[0,[]],5]
[357:044] 0x7fab6977e360: F->C: ["trstate","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"a":{"rtt":28},"allWritable":true,"anyRelay":false,"anyTcp":false,"anyWritable":true,"smoothedBWRecv":0,"smoothedBWSend":40637,"v":{"rtt":28}}]
[357:077] 0x7fab6977e360: F->C: ["jai","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",0,[0,[]],5]
[358:679] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":108,"s":0,"t":"a"}]
[359:680] 0x7fab6977e360: F->C: ["fw","muvc-private-chat-9999bae1-885d-4436-fd67-1fcd62df8a84@groupchat.google.com","c1492350838998505063",{"c":1,"s":0,"t":"a"}]
```

---

