---
title: "No sound in minecraft v1.16.1, Error initializing SoundSystem"
date: 2020-08-09
forum: General Help
---

### Post by androygaming on 2020-08-09
I am new to ubuntu and this community and noob too XD. So I installed minecraft yesterday and its working great. I just have one problem that I cant hear any sound from speakers. I am using laptop so there isnt any external speaker. Here are the logs I took from latest.log in .minecraft/logs dir

```
[12:17:35] [main/ERROR]: Error starting SoundSystem. Turning off sounds & music
java.lang.IllegalStateException: Failed to open OpenAL device
    at dfu.g(SourceFile:211) ~[dfu.class:?]
    at dfu.a(SourceFile:136) ~[dfu.class:?]
    at epk.g(SourceFile:99) [epk.class:?]
    at epk.a(SourceFile:90) [epk.class:?]
    at epn.a(SourceFile:116) [epn.class:?]
    at epn.a(SourceFile:39) [epn.class:?]
    at abf.a(SourceFile:13) [abf.class:?]
    at abf$$Lambda$2597/1610476156.accept(Unknown Source) [abf.class:?]
    at java.util.concurrent.CompletableFuture.uniAccept(CompletableFuture.java:656) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture$UniAccept.tryFire(CompletableFuture.java:632) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture$Completion.run(CompletableFuture.java:442) [?:1.8.0_51]
    at abg.a(SourceFile:71) [abg.class:?]
    at abg$$Lambda$2789/1379537056.run(Unknown Source) [abg.class:?]
    at amn.execute(SourceFile:94) [amn.class:?]
    at abg.a(SourceFile:70) [abg.class:?]
    at abg$$Lambda$2584/706752256.execute(Unknown Source) [abg.class:?]
    at java.util.concurrent.CompletableFuture$UniCompletion.claim(CompletableFuture.java:529) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture.uniAccept(CompletableFuture.java:653) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture$UniAccept.tryFire(CompletableFuture.java:632) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture.postComplete(CompletableFuture.java:474) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture.postFire(CompletableFuture.java:561) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture$UniAccept.tryFire(CompletableFuture.java:635) [?:1.8.0_51]
    at java.util.concurrent.CompletableFuture$Completion.run(CompletableFuture.java:442) [?:1.8.0_51]
    at elw$$Lambda$2792/809911552.execute(Unknown Source) [elw.class:?]
    at com.mojang.blaze3d.systems.RenderSystem.replayQueue(SourceFile:116) [RenderSystem.class:?]
    at com.mojang.blaze3d.systems.RenderSystem.flipFrame(SourceFile:103) [RenderSystem.class:?]
    at dgy.e(SourceFile:308) [dgy.class:?]
    at dlx.e(SourceFile:1041) [dlx.class:?]
    at dlx.e(SourceFile:654) [dlx.class:?]
    at net.minecraft.client.main.Main.main(SourceFile:215) [Main.class:?]
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[?:1.8.0_51]
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[?:1.8.0_51]
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[?:1.8.0_51]
    at java.lang.reflect.Method.invoke(Method.java:497) ~[?:1.8.0_51]
    at org.tlauncher.Launch.launch(Launch.java:156) [tl_skin_cape_1.16.1-1.11.jar:?]
    at org.tlauncher.Launch.main(Launch.java:24) [tl_skin_cape_1.16.1-1.11.jar:?]
```


I tried lots of stuff to resolve from other threads, there were not much thread on this topic
Also, sounds not working in any of version of minecraft
the versions I tried are v1.16.1, v1.10, v1.14.2 and more I dont remember lol

1.
```
padsp java -jar minecraft.jar
```

2.
Open this file(or create if not exists
```
/etc/openal/alsoft.conf
```
and change drivers to this
```
drivers=alsa
```

3.
Tried to reload resources in game using  F3+T combo 

These solutions didn't work and my sound is working properly on firefox and all. Someone please give me solution to this :)

---

### Post by Yellow Pasque on 2020-08-09
Should be "drivers=pulse"
Also, check output of openal-info
```
sudo apt-get install openal-info
openal-info
```

---

### Post by androygaming on 2020-08-09
Alright it worked :) also I was doing a mistake I was running minecraft launcher with root. After doing ur codes and running as non root user problem solved, thanks for help :D

---

