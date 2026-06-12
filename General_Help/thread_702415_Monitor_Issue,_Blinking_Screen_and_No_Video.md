---
title: "Monitor Issue, Blinking Screen and No Video"
date: 2008-02-20
forum: General Help
---

### Post by LaRoza on 2008-02-20
My monitor, a Benq 22" LCD, suddenly stopped displaying video. When it is on, and the computer is on, it blinks a full white screen, whith a full black screen. It is a slow cycle, and there is no hint of anything else.

It does this with any cables, on any computer.

The power works, the back light works, and the connection works. Does anyone know why it won't display correctly?

I changed no settings on the monitor, and even that menu won't display.

---

### Post by freelinuxhelp on 2008-02-20
You've tried different cables and different computers with this monitor? If so, does the on-screen configuration work? If not, I'd try to get an RMA from the manufacturer.

---

### Post by LaRoza on 2008-02-20
> **freelinuxhelp said:**
> You've tried different cables and different computers with this monitor? If so, does the on-screen configuration work? If not, I'd try to get an RMA from the manufacturer.

Yes, that is what I did first.

The menu doesn't come up at all.

Because I bought this from another person (that I trust, still do), the manufacturer's warrenty is not an option.

It happened suddenly, when I went to restart the computer. Such is life. I have my old one, which is still good.

---

### Post by firecrow8 on 2008-03-11
I had the same issue and I fixed it with
[B]
noapic nolapic[/B]

it's a monitor/graphics card issue and ubuntu must be detecting the wrong one.

once I found the above commands and added the to the end of my boot string

(pres f6 at the ubuntu boot options screen add "noapic nolapic" without "")

it's worked fine

---

