---
title: "Japanese language &amp; region missing from 22.04"
date: 2022-04-27
forum: General Help
---

### Post by riquez2 on 2022-04-27
Hi, 
I have a Japanese laptop & currently run Ubuntu 21.10 with a mix of English & Japanese language & region settings. (KB: JP, lang: EN, formats: JP)
I have been doing so for about a year without any trouble.

Checking the liveCD of Ubuntu 22.04 the option for **Japanese region is missing in the Formats**. To me this is important because Japanese dates are YY MM DD & this is what I am used to.

Also,* I don't know if this is related,* but I can NOT select an alternative characters key. I'm trying to choose 'Right CTRL' but it refuses, & reverts to NONE.
I have selected the KB to be Japanese & that seems to be correct, it shows the correct layout. But I need to be able to choose 'Right CTRL' since my KB doesn't have any other suitable modify key.
My keyboard is not unusual, it's a fairly recent Lenovo with a standard Japanese layout.

---

### Post by him610 on 2022-04-27
> Japanese dates are YY MM DD & this is what I am used to.
I did not know that was the preferred way of Japanese dates.
I have been writing my dates in the YYMMDD format for years. It makes so much sense; the dates are a lot easier to sort too.
Hope you find a solution.

---

### Post by riquez2 on 2022-04-27
Yes, I agree, it does make things easier, especially with computers (numerically). In Japan they usually organise things from Big -> small. Postal address order is: State, City, Street, House. Which if you think about it makes more sense for delivery.

I did find a solution!  - I installed the Japanese Language pack**  (settings > lang & region > language {manage installed langs}) **& then the date formats were also available in Japanese. :-)
I should have tried that first, but there were already many international date formats, I couldn't realise why not Japan. But now I understand.

As for the Alternative Characters Key - I am still unable to choose `Right Ctrl` I don't know why, but it doesn't seem related to language.

---

### Post by Impavidus on 2022-04-28
> **him610 said:**
> I have been writing my dates in the YYMMDD format for years. It makes so much sense; the dates are a lot easier to sort too.
If you care about the background, some languages are mostly head-initial in possessive constructions and other are mostly head-final. English, like most European languages, is mostly head initial: we say "the wheel of the car", not "of the car, the wheel". Similarly, we say "This day is the 28th day of the month April of the 2022nd year", not "This day is of the 2022nd year, of the month April, the 28th day". That's why day-month-year makes most sense to most Europeans (English is a bit weird here, as some English speakers prefer a mixed order: month-day-year).

Japanese is mostly head-final, so it reverses the order: year-month-day. Computers are pretty bad at processing natural language, so they have a hard time sorting dates in any way other than alphabetic.

If the issue has been solved, could you mark the thread as solved?

---

### Post by riquez2 on 2022-04-28
Thanks @Impavidus for those fascinating details. (marked as solved!)

It's funny though, isn't it, that Calendars are always head-final. We buy them by Year, turn pages by Month & then finally note the Day. It would be absurd to imagine it in reverse, & yet that is how we arrange it in English language. 
We do head-final for all types of measurements, but not in natural speech.

---

