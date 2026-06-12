---
title: "wine dll question."
date: 2023-04-30
forum: General Help
---

### Post by ulao3 on 2023-04-30
I was curios if anyone knows how to allow an exe to access a local dll file using a c# app via "DllImport".

I wrote an app that access hidapi.dll using the [DllImport] with associated c file. the app run great but clearly has no access to the dll. I played with a few things I read online with no luck. the winetrick didn't know of hidapi but no surprise there. Any ideas? No big deal just playing with wine here to learn more about it.

---

### Post by TheFu on 2023-04-30
Place the DLL into the same directory as the EXE file.  By default, MS-Windows will look first for any needed DLLs in the same directory as the program, before checking the environment variables and system settings.

I've never done anything specific to make my code work under WINE.

---

### Post by ulao3 on 2023-04-30
yeah did that, so maybe its just that hidapi will not work with wine then. Interestingly its linux counter part is libusb, but no convert has been done yet I guess. Unless I need to install some type of HID driver?

---

