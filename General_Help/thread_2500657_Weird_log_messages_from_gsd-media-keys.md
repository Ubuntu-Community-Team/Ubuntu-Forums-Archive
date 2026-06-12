---
title: "Weird log messages from gsd-media-keys"
date: 2024-09-08
forum: General Help
---

### Post by abrandemuehl on 2024-09-08
The following is for ubuntu 22.04.4 LTS on 6.8.0-40-generic and an intel laptop.

Hey all, while looking through my syslog to diagnose some screen freezing, I noticed some really weird log messages with the identifier gsd-media-keys

See following:

```

Sep 05 21:02:48 laptop gsd-media-keys[2039]: [2140:2146:0905/210248.189433:ERROR:socket_manager.cc(147)] Failed to resolve address for turn2-84f4cbd976-728xw-euc1.media.prod.tokbox.com., errorcode: -105
Sep 05 21:02:48 laptop gsd-media-keys[2039]: [2140:2146:0905/210248.189494:ERROR:socket_manager.cc(147)] Failed to resolve address for turn2-84f4cbd976-728xw-euc1.media.prod.tokbox.com., errorcode: -105
Sep 05 21:02:48 laptop gsd-media-keys[2039]: [2140:2146:0905/210248.230749:ERROR:socket_manager.cc(147)] Failed to resolve address for turn2-84f4cbd976-728xw-euc1.media.prod.tokbox.com., errorcode: -105
...
Sep 08 16:38:21 laptop gsd-media-keys[2180]: Created TensorFlow Lite XNNPACK delegate for CPU.

...
Sep 08 16:38:30 laptop gsd-media-keys[2180]: Attempting to use a delegate that only supports static-sized tensors with a graph that has dynamic-sized tensors (tensor#58 is a dynamic-sized tensor).

```

I don't believe that gsd-media-keys should be loading tensorflow and pinging what appears to be a video streaming provider, so I'm assuming that the systemd log is somehow attributing these log messages to the wrong identifier. 

I assume these are actually google chrome messages, wrongly attributed somehow to gsd-media-keys as the networking lines look like chrome log messages.

Also, if I grep from my root directory for the gsd-media-keys string, I see a file

```
# /run/user/1000/systemd/transient/app-gnome-google\x2dchrome-2173.scope
# This is a transient unit file, created programmatically via the systemd API. Do not edit.
[Unit]
Description=Application launched by gsd-media-keys
CollectMode=inactive-or-failed

```



Has anyone else seen things like this? Just want to make sure I'm not crazy and gsd-media-keys is doing what I expect. Any insight is appreciated!

---

### Post by abrandemuehl on 2024-09-10
I've thought about it a bit more, and my best guess is that I'm starting google chrome with the media key shortcut for open web browser. So it would make sense that gsd-media-keys is launching the browser, and the log identifier is just being propagated to the child process. I'll mark this solved, as it makes sense to me and it doesn't worry me that something is going horribly wrong.

---

