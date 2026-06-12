---
title: "anysee digibox doesn't work with my computer"
date: 2008-02-14
forum: General Help
---

### Post by crazyfuturamanoob on 2008-02-14
I just bought anysee E30C+ usb digibox for my computer. There was a cd with the digibox.
The thing I bought and am talking about is for watching tv on computer, if some1 doesn't know.
I installed the software from the cd. Then I attached the digibox to a random usb port.
I launched the app for watching tv. It said "no channels. scan channels first.". I clicked  "quick scan",
and then it quit working at all, any buttons didn't work, and it gave this before crashing:
> Access violation at adress 7B9BAE02 in module 'quartz.dll'.
Read of adress 00000000.
Any ideas getting it work? I read the manual, and there was instructions for windows xp:
> plug the digibox to a usb port and wait until windows detects it automatically.
Then it should popup a driver installer blahblahblah... click next...
It was something like that. How can I install it to wine?
Help! How to get it working?

---

### Post by crazyfuturamanoob on 2008-02-15
Anyone?

---

### Post by crazyfuturamanoob on 2008-03-02
Not even a single reply? Where are you? I need help with this.
My wine version is 0.9.46. I'll give thanks for first post.

---

### Post by crazyfuturamanoob on 2008-03-04
I got this from winedebug:
> 
fixme:process:IsWow64Process (0xffffffff 0x34f940) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecdc,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x154ff8)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x154ff8)->((nil),00000008)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {65e8773d-8f56-11d0-a3b9-00a0c9223196} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {65e8773d-8f56-11d0-a3b9-00a0c9223196} not found
fixme:win:SetLayeredWindowAttributes (0x101d2,0x00000000,255,1): stub!
fixme:win:SetLayeredWindowAttributes (0x101f0,0x00000000,255,1): stub!
fixme:win:SetLayeredWindowAttributes (0x201de,0x00000000,255,1): stub!
fixme:win:SetLayeredWindowAttributes (0x1020c,0x00100010,255,1): stub!
fixme:win:SetLayeredWindowAttributes (0x20026,0x00000000,255,1): stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {a799a801-a46d-11d0-a18c-00a02401dcd4} not found

edit: lol turn smileys off to see the correct text

---

