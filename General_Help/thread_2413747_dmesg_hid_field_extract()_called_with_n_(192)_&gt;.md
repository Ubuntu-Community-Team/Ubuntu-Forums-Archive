---
title: "dmesg: hid_field_extract() called with n (192) &gt; 32! (kworker/5:5)"
date: 2019-03-01
forum: General Help
---

### Post by fmstrat2 on 2019-03-01
My dmesg is getting filled up with:

```
[  437.796725] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.796728] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896804] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896809] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896813] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896816] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996600] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996606] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996610] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
```

Anyone have any ideas how to debug this?

---

### Post by bjlockie on 2019-03-01
Is that a USB  device?

---

### Post by vidtek on 2019-03-02
> **fmstrat2 said:**
> My dmesg is getting filled up with:

```
[  437.796725] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.796728] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896804] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896809] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896813] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.896816] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996600] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996606] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
[  437.996610] hid-sensor-hub 001F:8086:22D8.0002: hid_field_extract() called with n (192) > 32! (kworker/5:5)
```

Anyone have any ideas how to debug this?

Start by physically changing the USB port into which you plug your mouse/keyboard.  Do one device at a time and look for dmesg changes after.
You should see which device is causing problems.   I have found that multi-port hubs are usually to blame, rarely the device itself.
Tony.

---

