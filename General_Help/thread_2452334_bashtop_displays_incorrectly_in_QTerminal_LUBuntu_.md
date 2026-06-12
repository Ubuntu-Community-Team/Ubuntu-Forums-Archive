---
title: "bashtop displays incorrectly in QTerminal LUBuntu 20.04.1"
date: 2020-10-20
forum: General Help
---

### Post by David_Partridge on 2020-10-20
I tried to include a screenshot but my post was rejected with a nastygram about a missing security token or some such.

I installed LxTerminal and bashtop displayed perfectly in an LxTerminal window.

David

---

### Post by David_Partridge on 2020-10-20
Managed to get a screenshot ...


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=287189&d=1603208685[/IMG]

---

### Post by guiverc on 2020-10-24
This is not limited to anything in Ubuntu, as I saw it last night using  `bpytop` on Debian Bullseye/Sid (it occurs there with `bashtop` too)

I also suspect it occurs in other shells too (not just QTerminal) as  I've seen it on systems where I wasn't using LXQt (including 18.04)  though it wasn't recent enough for me to recall details.

It never worried me enough to look for a pattern (or thus cause).

---

### Post by GhX6GZMB on 2020-10-24
I'm probably dense, but which part displays incorrectly? Your screenshot looks nice to me.

---

### Post by guiverc on 2020-10-24
I took it as the vertically bars not lining up.

I just noticed my background for one monitor (which is a cool-retro-term running as a snap) on my Lubuntu *hirsute* system also has the flaw (*and far worse*). It's a very different program, and cool-retro-term for me is using the ibm-3278 font (*I'm an ex-mainframe guy, if it needs explanation*)

@David   FYI: I replied via LP because I saw it there first (*the bug hit my email inbox*). We were focussing on *groovy* hitting the streets, so watching support places hasn't been high priority in recent days.. I plan to find our where I saw/see it on *bionic* next, but it's not high priority.

---

