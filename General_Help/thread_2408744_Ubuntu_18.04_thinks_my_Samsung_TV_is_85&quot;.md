---
title: "Ubuntu 18.04 thinks my Samsung TV is 85&quot;"
date: 2018-12-22
forum: General Help
---

### Post by iamtheliquor on 2018-12-22
Hi everybody,

I have a Samsung UE55NU7100 55-Inch 4K Ultra HD (2018) TV, and when connected via the HDMI cable, Ubuntu thinks it is an 85" screen. This causes the display to be very choppy and also extend off the edge. Other 4k displays via HDMI are fine, I've tested a few with no such issues, so I've got a sneaking suspicion the TV will be blamed. There are no options I can change via the TV, the picture options are limited, it's setting it to 16:9 and I cannot change from that when connected via HDMI, other than custom which just allows me to zoom or move the picture. That doesn't resolve anything.

Please see attached images to show what I mean.

Just chucking it out there in case anyone has any fancy suggestions that might fix this?

---

### Post by vidtek on 2018-12-22
> **iamtheliquor said:**
> Hi everybody,

I have a Samsung UE55NU7100 55-Inch 4K Ultra HD (2018) TV, and when connected via the HDMI cable, Ubuntu thinks it is an 85" screen. This causes the display to be very choppy and also extend off the edge. Other 4k displays via HDMI are fine, I've tested a few with no such issues, so I've got a sneaking suspicion the TV will be blamed. There are no options I can change via the TV, the picture options are limited, it's setting it to 16:9 and I cannot change from that when connected via HDMI, other than custom which just allows me to zoom or move the picture. That doesn't resolve anything.

Please see attached images to show what I mean.

Just chucking it out there in case anyone has any fancy suggestions that might fix this?

I have a UA55ES8000 and stuffed around with screen scaling with nvidia for ages before finding a setting in the tv's menu itself to scale computer inputs.  Yours will be the same.
Cheers, Tony.

---

### Post by iamtheliquor on 2018-12-22
Thanks Tony, even though you didn't give me the specific answer, you did prompt me to take another look, and deep within the settings I found 'HDMI UHD Color'. Apparently without this switched on the HDMI inputs will only work up to 1080p. All working fine now.

---

