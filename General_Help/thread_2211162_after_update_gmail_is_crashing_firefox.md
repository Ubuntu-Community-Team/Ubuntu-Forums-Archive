---
title: "after update gmail is crashing firefox"
date: 2014-03-14
forum: General Help
---

### Post by danielsender on 2014-03-14
I'm running 12.04 LTS and after the last update whenever I open gmail, firefox crashes. I tried re-installing firefox, removing all extensions and didn't help. I also deleted the whole .mozilla folder. On the other hand, gmail works fine with Chrome.

Thanks.

---

### Post by danielsender on 2014-03-15
I ran firefox from a terminal with the gdb debugger (firefox -d gdb), I'm attaching it here.

```
No bp log location saved, using default.
[000:000] Cpu: 15.0.7, x1, 1395Mhz, 2013MB
[000:000] Computer model: Not available
[000:001] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:002] Using Gtk2 toolkit
[000:043] Starting client channel.
[000:044] Warning(clientchannel.cc:472): 0xb75b9790: Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:045] 0xb75b9790: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "error" : -1,
        "step" : "0"
    }
]

[000:048] Warning(clientchannel.cc:445): 0xb75b9790: Could not initiate GoogleTalkPlugin connection
[000:048] 0xb75b9790: GoogleTalkPlugin not running. Starting new process...
[000:048] Starting Flute
[000:048] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:048] Warning(pluginutils.cc:268): Failed to get GoogleTalkPlugin path. Trying default.
[000:053] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:053] 0xb75b9790: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "2"
    }
]

[000:055] 0xb75b9790: Waiting for GoogleTalkPlugin to start...
[001:112] 0xb75b9790: Attempting to connect to GoogleTalkPlugin...
[001:113] Read port file, port=52694
[001:113] 0xb75b9790: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "0"
    }
]

[001:574] 0xb753e520:  sending cookie icPjf2ZbNstoQD7b
[001:575] 0xb75b9790: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "1"
    }
]

[001:753] 0xb75b9790: Initiated connection to GoogleTalkPlugin
[001:754] 0xb75b9790: SendConnectStatus: Connect Status: 
[
    "f-connect",
    
    {
        "step" : "3"
    }
]

[002:021] 0xb75b9790: Socket connection established
[002:022] 0xb75b9790: ScheduleOnlineCheck: Online check in 5000ms
[002:123] 0xb753e520: Got cookie response, socket is authorized
[002:124] 0xb75b9790: AUTHORIZED; socket handshake complete
[002:228] 0xb75b9790: C->F: ["mf",2,{"appName":"googlemail","buildLabel":"gmail_fe_140311.00_p3","buildCl":"63063784","compileMode":"OPTIMIZED,LOCALE=en","estimatedBwBps":"1219656.4506425897","numBwDataPoints":"4","setup_timeout":90000,"exps":[],"jid":"daniel.senderowicz@gmail.com","renderer":2,"useBrowserHttp":true,"o3dVersion":"0.1.44.29","domain":"mail.google.com","useragent":"Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:27.0) Gecko/20100101 Firefox/27.0","pluginversion":"5.1.5.0"}]
[002:244] 0xb75b9790: F->C: ["fs",{"pr":"a"}]
[002:370] 0xb75b9790: F->C: ["mf","mf5.1","5.1.5.0",2,{"audioCodecs":[[103,"ISAC",1,0,16000],[111,"opus",2,64000,48000],[104,"ISAC",1,0,32000],[109,"CELT",1,64000,32000],[110,"CELT",2,64000,32000],[9,"G722",1,64000,16000],[102,"ILBC",1,13300,8000],[0,"PCMU",1,64000,8000],[8,"PCMA",1,64000,8000],[106,"CN",1,0,32000],[105,"CN",1,0,16000],[13,"CN",1,0,8000],[127,"red",1,0,8000],[126,"telephone-event",1,0,8000]],"audioRtpHdrExts":[{"id":1,"uri":"urn:ietf:params:rtp-hdrext:ssrc-audio-level"}],"camDeviceName":"Unknown Camera","caps":7,"cpuAdaptVersion":1,"cpuArchitecture":0,"cpuCacheSize":262144,"cpuFamily":15,"cpuFlags":["sse2"],"cpuHasSSE2":true,"cpuModel":0,"cpuSpeed":1395,"cpuStepping":7,"cpuVendor":"GenuineIntel","cpus":1,"cpusPhysical":0,"cryptoRandom":"PPr1jJjonc3Rx/v/XxD50vFp","cryptoSuites":["AES_CM_128_HMAC_SHA1_80","AES_CM_128_HMAC_SHA1_32"],"dataChannelVersion":1,"effectsVersion":11,"gpuDescription":"","gpuDeviceId":0,"gpuDeviceName":"","gpuDriver":"","gpuDriverVersion":"","gpuVendorId":0,"machineModel":"Not available","remotingAssistanceAllowed":1,"remotingVersion":1,"renderer":2,"rtcpMux":true,"screencast":2,"screencastLocalPreview":1,"supportsConcurrentSessions":true,"transports":["i","gice"],"videoCodecs":[[100,"VP8",640,400,30],[116,"red",640,400,30],[117,"ulpfec",640,400,30],[99,"H264-SVC",640,360,30],[97,"H264",640,360,30],[98,"H263",640,360,30]],"videoRtpHdrExts":[{"id":2,"uri":"urn:ietf:params:rtp-hdrext:toffset"},{"id":3,"uri":"http://www.webrtc.org/experiments/rtp-hdrext/abs-send-time"}],"vsVersion":1}]
[003:219] 0xb75b9790: C->F: ["getdevicestate"]
[003:329] 0xb75b9790: F->C: ["getdevicestate","15","0",["__default_device","ES1371 [AudioPCI-97] Analog Stereo"],"0",["__default_device","ES1371 [AudioPCI-97] Analog Stereo"],"-1",[]]
WARNING: pipe error (3): Connection reset by peer: file /build/buildd/firefox-27.0.1+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 446

###!!! [Child][MessageChannel::InterruptCall] Error: Channel error: cannot send/recv
```

Thanks.

---

### Post by danielsender on 2014-04-19
I sent the problem to the firefox launchpad but I haven't got any answer yet. This is becoming more weird. I just upgraded from 12.04 to 14.04, completely remove firefox and re-installed and the problem remains. I disabled the add-ons and even ran the program while kneeling down and nothing. Can a good soul give me a pointer?

---

### Post by bapoumba on 2014-05-16
[http://ubuntuforums.org/showthread.php?t=2224490](http://ubuntuforums.org/showthread.php?t=2224490)
Current thread, closing here.

---

