---
title: "Hylafax blacklists"
date: 2015-01-29
forum: General Help
---

### Post by manthony121 on 2015-01-29
My office uses a computer running Ubuntu 10.04.4 LTS and hylafax, with an external modem, as our fax server.  The system works well, but there is one office that tries to send us faxes, and results in hylafax going into an unending "Receiving fax from...." state.  No fax is ever received, and we usually re-boot the server to get things back to normal.  I don't know what it is about that sender's fax system that causes ours to hang.  I would like to block our system from receiving calls from that number, to prevent this problem in the future.

I came across the option for "Per-call dynamic configuration" in the hylafax advanced server configuration guide.  It describes a way to write a small script that will reject calls from a particular number.  Does anyone have experience using this option?  I am about to start working on it, and any advice would be welcome.

---

### Post by Li_Wu on 2015-09-17
have you tried a different modem? like US Robotics usb modem? may make sense

---

