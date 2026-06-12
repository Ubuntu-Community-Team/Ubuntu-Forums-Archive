---
title: "terminal not stopping after opening google chrome"
date: 2013-02-01
forum: General Help
---

### Post by symaticc on 2013-02-01
Hi, I am fairly new to ubuntu and I was wondering. After I open the terminal and open either google-chrome or chromium-browser through the terminal, chromium opens but the terminal continues to run and doesn't stop. It gives me these errors:

[4241:4241:0201/192619:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(gfx::NativeView)
[4241:4241:0201/192641:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(gfx::NativeView)

and it goes on and doesn't stop until I close chromuim or kill the terminal, which ends up closing chromium as well. I was wondering how I fix this problem?

Thanks in advance!

---

### Post by papibe on 2013-02-01
Hi symaticc.

That behaviour is normal.

When you run a program on the terminal, it waits until the program ends to return to an interactive prompt.

The messages you are seeing are not errors but warnings or debug messages.

There's a way to "disconnect" what you run on the terminal, so you get the prompt immediately back:
```
chromium-browser &
```
That '&' in the end tells the terminal to run chromium on the background independent of the terminal.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by symaticc on 2013-02-02
Hm, I typed that into the terminal but still nothing happened, it continued running :/

I took a screenshot of it and it is in the attachments.

---

### Post by papibe on 2013-02-02
You have to type that instead of the regular command.

This:
```
chromium-browser &
```
Not this:
```
chromium-browser
```
And definitely not this:
```
chromium-browser
chromium-browser &
``` 
Let us know how it goes.
Regards.

---

### Post by symaticc on 2013-02-02
ohhh okay awesome, thanks! It worked!

---

