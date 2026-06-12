---
title: "Developing for Win32 in Ubuntu"
date: 2008-01-06
forum: General Help
---

### Post by Mathijsken on 2008-01-06
Hey everyone!
I'm looking up some information on developing in Ubuntu (or Linux for that matter) for a Win32 platform. I've found the great Mono project that I believe, will suit most of my needs, however there's one thing I couldn't find too much information about, (cross-platform) Audio Support!

Reason for this I would develop an image viewer with the abbility to add (recorded) sound fragments. I have a physically handicapped nephew who would benefit from such a program, as he would be able to learn to connect certain words and names with the person/object/phenomena/...
It would als allow him to click through these pictures himself (using a giant mouse button), make little stories he can watch & listen too. It would be my way of helping him and a good way to sharpen my programming skills.

Blah-di-blah, if anyone knows of good Audio Libraries (incorporated into Mono?) please let me know!
(if this is posted in the wrong place, feel free to move!)
greetz,
Mathijs

---

### Post by dlegend on 2008-01-06
> **Mathijsken said:**
> Hey everyone!
I'm looking up some information on developing in Ubuntu (or Linux for that matter) for a Win32 platform. I've found the great Mono project that I believe, will suit most of my needs, however there's one thing I couldn't find too much information about, (cross-platform) Audio Support!

Reason for this I would develop an image viewer with the abbility to add (recorded) sound fragments. I have a physically handicapped nephew who would benefit from such a program, as he would be able to learn to connect certain words and names with the person/object/phenomena/...
It would als allow him to click through these pictures himself (using a giant mouse button), make little stories he can watch & listen too. It would be my way of helping him and a good way to sharpen my programming skills.

Blah-di-blah, if anyone knows of good Audio Libraries (incorporated into Mono?) please let me know!
(if this is posted in the wrong place, feel free to move!)
greetz,
Mathijs

I'm not sure if that is possible. I haven't done any Linux programming but the APIs that Mono uses I believe are much different then what Microsoft's .NET uses. I don't think they can translate onto the Win32 platform. I think if you want to write Windows applications you will have to stick with coding in Windows, otherwise use java / some form of web language.

---

