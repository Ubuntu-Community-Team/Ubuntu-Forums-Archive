---
title: "Problem with encoding Chinese fonts in emails"
date: 2006-12-08
forum: General Help
---

### Post by VincentLC on 2006-12-08
This problem is probably very rare to encounter but I'm giving it a try.

I often send emails that are in Chinese to friends of mine, and I get no encoding problems. If I also add English text, everything is still fine, but as soon as I add a special French character (accent, cedilla or diaresis), while at the same time using Chinese text, then it looks like no encoding can take it all and the receivers of my email get those weird characters you get all over the text when encoding is incorrect -- to me, everything always looks fine. Actually, all Chinese characters are incorrectly displayed and special French characters only are incorrectly displayed.

I tried this using both Gmail and Yahoo. None works. Traditional or simplified characters has nothing to do. I know what Unicode is, but if I force it, the problem remains (actually expands to all emails, even French-only ones). Anyways, I wouldn't want to add a signature which says 'Please set your browser to Unicode, here's how to if you don't know what that is!' My LC_CTYPE is zh_TW.UTF-8 but all other locale settings are fr_CA. I've also tried, without success, to set everything to zh_TW.

Now, this probably has nothing to do, but I also noticed this thing in any page that is not Chinese per se but has Chinese text in it (for example, my Gmail inbox or Wikipedia when the Western-language article includes a Chinese word in brackets). What happens is that all characters that are Tradidional or the same in Traditional and Simplified are rendered in a given font, while characters that are strictly Simplified are rendered in a different font. Why is that? Is there some 'default' system Chinese font which supports Big-5 and another, alternate, one for all unsupported characters in Big-5? If there is, can this be changed?

Thanks anyone!

---

