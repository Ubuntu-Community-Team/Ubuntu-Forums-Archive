---
title: "How to display large text, lyrics-style?"
date: 2015-02-05
forum: General Help
---

### Post by Paddy Landau on 2015-02-05
I have a seemingly-simple requirement.

I wish to display large and clear text that changes after set times, in the same way as lyrics display for a song.

For example, display text set 1 for 17 seconds, then text set 2 for 5 seconds, then text set 3 for 12 seconds, and so on.

Each text set will be just a few lines, or only one line.

I would like, either full-screen or maximised, the text to be large and black against a white background, left-justified, starting at the top of the screen.

I need nothing fancier than that — no scrolling. An option for coloured backgrounds for specified text would be nice, but is not necessary.

These aren't lyrics, so no music will be playing.

Question:

What is the easiest way to achieve this? Do I have to write some script with some type of display mechanism? Or does an application already exist for this? I don't mind whether the solution uses a browser or a native app. (I don't know HTML 5, Javascript, or how to write plugins, so I can't use those if I have to write my own script. I only know Bash and a *small* amount of HTML 4 and PHP.)

Thank you.

---

### Post by Holger_Gehrke on 2015-02-05
I'd just fire up LibreOffice Impress. It's overkill, but it should be able to do this easily.

---

### Post by Paddy Landau on 2015-02-05
> **Holger_Gehrke said:**
> I'd just fire up LibreOffice Impress. It's overkill, but it should be able to do this easily.
Thank you; I've just tested it and it works.

It's slow entering the details especially when there are many sets of text with different times. I was hoping for a faster editing process, but as you say, it works: I'll use it if something simpler doesn't come along. (Interestingly, it doesn't allow the option of a background colour to selected text.)

---

### Post by Holger_Gehrke on 2015-02-05
> **Paddy Landau said:**
> Interestingly, it doesn't allow the option of a background colour to selected text.

Just put a page-sized coloured rectangle behind the text.

---

### Post by Paddy Landau on 2015-02-05
I've figured out an easier method, although I had to write a simple script.

I use [FONT=lucida console]yad[/FONT], maximised, to display a full screen with large text. The script simply reads each line and either pauses (if the line contains only a number) or sends the line to [FONT=lucida console]yad[/FONT].

It cannot show colour, unfortunately, but at least the editing is easy now; I shall have plenty of text to write.

---

