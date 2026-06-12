---
title: "s.t.a.l.k.e.r (game) with wine install help"
date: 2007-03-19
forum: General Help
---

### Post by whorobj on 2007-03-19
```
rob@rob-desktop:~$ wine /media/iso/setup.exe
fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x34fe9c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x170cb0 0x34fe1c) stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1bde80) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x185a90)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:win:EnumDisplayDevicesW ((null),0,0x34e774,0x00000000), stub!
**wine: Call from 0x7b8405f0 to unimplemented function shell32.dll.SHPathPrepareForWriteA, aborting**

```

I get to the part of the installer where it shows the directory then you hit install and i get the above error.

ideas?

---

### Post by crispy_420 on 2007-03-19
That's odd as the game has yet to come out, release date is March 21. Did it get released outside US sooner?

---

### Post by whorobj on 2007-03-19
it's out on torrents and newsgroups

---

### Post by helmet on 2007-03-19
> **crispy_420 said:**
> That's odd as the game has yet to come out, release date is March 21. Did it get released outside US sooner?

yeah no kidding...if you're going to pirate a game, at least do it on the platform it was designed for and don't ask questions on a bloody linux forum...

---

### Post by helmet on 2007-03-19
> **whorobj said:**
> it's out on torrents and newsgroups

because that makes it totally cool and alright...

---

### Post by whorobj on 2007-03-19
i'm having a problem with wine, and im aksing for help. Isn't that what this forum is for? If you're not going to help dont post.

---

### Post by helmet on 2007-03-19
my point is this is a forum for help with ubuntu related problems. your problem is you can't play a game, which, while we can't prove, we can probably say you didn't get legally, considering the game isn't out yet. unless you have the beta this for some reason.

anyway....the wine problem seems obvious....the installer is trying to do something for which wine does not have support for. are you running the latest wine?

---

### Post by whorobj on 2007-03-19
it wont let me upgrade to 3.3 im running 2.2

I have this problem

When I try to upgrade to the latest version of wine (0.9.33) in the Synaptic Package manager I get the following error:

wine:
Depends: libgphoto2-2 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed
Depends: libgphoto2-port0 (>=2.3.0) but 2.2.1-2ubuntu4 is to be installed

both are installed and up to date.

---

### Post by whorobj on 2007-03-19
anyone?

---

### Post by redsmoke on 2007-03-22
try changing windows version to 98 in winecfg and it should work.

---

### Post by redsmoke on 2007-03-23
of course the game doesn't work after install at least for me anyways. crashes out. And no windows partition for me to try the real deal :P oh well...I guess i will have to wait for wine to catch up. Haven't tried cedega cvs but i assume same result.

---

### Post by bvidinli on 2007-03-30
thank you for your offer,
i am able to run delphi by setting windows as win2000 instead of winxp

as i understand, lower the windows version, more chance to run a windows program since more compatibility..
thanks.

---

