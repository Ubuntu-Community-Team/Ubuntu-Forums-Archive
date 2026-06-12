---
title: "Kill Quicksynergy ?"
date: 2013-12-30
forum: General Help
---

### Post by sarahfoxnz on 2013-12-30
Hello. How do i kill / Stop QUICKSYNERGY ?

basically, i'm trying to activate Synergy as a server on my UBUNTU box, but it cannot bind / assign to my address.

I have done this command :-

> 
ps -ef | grep synergy

sarah    8411     1  1 14:55 ?        00:00:21 synergys -c /home/sarah/.quicksynergy/synergy.conf


quicksynergy is already running, but i CAN find a way to kill "synergys" - but quicksynergy still running.

---

### Post by sarahfoxnz on 2013-12-30
Hello.

i've mangeg to kill my other quicksynergy. However i have a new problem.

in my WIn8 synergy, (version 1.4.15) it has an error - "incompatible client 1.3".

The version on my ubuntu box (i want s server), is 1.3  - I tried to re-install it on ubuntu, but the version is still 1.3

in various google searches i saw a reference that the above error occurs with different versions, and ALL synergy programmes need to be the same version.

is this correct ?  how to i upgrade my ubuntu version of synergy to 1.4.15 ?

(Ps, is there a way to edit the subject / title of these forum posts ?)

---

### Post by claracc on 2013-12-31
What ubuntu are you using? 12.04, 13.04, 13.10?.

I have found ppa repository in launchpad for sinergy package: [https://launchpad.net/ubuntu/+source/synergy](https://launchpad.net/ubuntu/+source/synergy), the 1.4.12 package seems to be (no 1.4.15) the more recent available in saucy salamander, and there is other ppa: [https://launchpad.net/~trebelnik-stefina/+archive/synergy](https://launchpad.net/~trebelnik-stefina/+archive/synergy) with 1.4.13 version release.

You can try to add the repository (follow the instructions, see the attached image) for your ubuntu release and see if it works.

---

### Post by sarahfoxnz on 2013-12-31
12.04 LTS.   Gnome 3.4.2

Thank you. i'll look those up & download the latest version of synergy

(I guess oneday my UPDATES area will tell me to install the next version of Ubuntu)

---

### Post by sarahfoxnz on 2013-12-31
Hi. Ive upgraded - here is the full info on my systems (if you want more, please ask)

> 
 synergys --version
synergys 1.4.12, protocol version 1.4
Copyright (C) 2012 Bolton Software Ltd.
Copyright (C) 2008-2012 Nick Bolton
Copyright (C) 2002-2012 Chris Schoeneman


when running the server i get this :-

> 
NOTE: stopping synergy desktop process
NOTE: starting server
NOTE: config file: /tmp/qt_temp.hc4275
NOTE: log level: NOTE
2013-12-31T21:10:56 NOTE: started server, waiting for clients
    /build/buildd/synergy-1.4.12/src/lib/synergy/CServerApp.cpp,613
2013-12-31T21:10:57 NOTE: accepted client connection
    /build/buildd/synergy-1.4.12/src/lib/server/CClientListener.cpp,147
2013-12-31T21:10:57 NOTE: new client disconnected
    /build/buildd/synergy-1.4.12/src/lib/server/CClientProxyUnknown.cpp,292
2013-12-31T21:11:01 NOTE: accepted client connection
    /build/buildd/synergy-1.4.12/src/lib/server/CClientListener.cpp,147
2013-12-31T21:11:01 NOTE: new client disconnected
    /build/buildd/synergy-1.4.12/src/lib/server/CClientProxyUnknown.cpp,292
NOTE: stopping synergy desktop process


(I trimmed a bit)..


the SERVER is Ubuntu 12.4 LTS. My other Pc is WIndows 8. 

Ubuntu is wired-connection with my router. my windows 8 Pc is Wifi connection to my router. (if that makes any difference)

in my synergy settings, I have :-

> 
screen name: windows
alias: WIN8   (the name of my PC)



---

### Post by claracc on 2013-12-31
Perhaps this thread: [http://synergy-foss.org/osqa/questions/3167/where-is-the-start-synergy-server-client-when-the-application-starts](http://synergy-foss.org/osqa/questions/3167/where-is-the-start-synergy-server-client-when-the-application-starts) can help you?

---

