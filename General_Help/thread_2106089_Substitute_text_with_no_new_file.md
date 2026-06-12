---
title: "Substitute text with no new file"
date: 2013-01-18
forum: General Help
---

### Post by Acharn on 2013-01-18
This is one of those things that, when I see the answer, I'm going to slap my forehead and groan, "I knew that!" It's not a pressing or important problem, but I can't think of appropriate keywords for a successful Google search. I have a collection of 53 HTML files, science fiction short stories and novelettes. All the ones I've checked so far have a link to a .jpg of the cover of the magazine they appeared in. I can't imagine why, but every one of those links that I've checked so far goes like: <a href="../images%5cTTC0168">. That '%5C' translates to the backslash character. What I want to do is mass substitution, changing 'images%5C" to 'images/'. I know how to do this with SED, but it would require making a new file for each one. I seem to recall there's a way to avoid doing that, but I can't remember and a quick glance at my SED tutorials doesn't show it up. Same with AWK or PERL. I could use any one of them, but can't remember how to not create a new file while doing it. I haven't used any of these tools for years. Of course I could open up each file in vi and do it that way, but it just seems so boring. So I'm hoping someone can remind me of the lazy man's way to do this.

---

### Post by lol on 2013-01-18
sed -i

'man' is your friend!

---

### Post by Acharn on 2013-01-19
LOL! You're absolutely right, and I'm glad you didn't reply "RTFM." I don't know if it's because of my age or because I've been corrupted by the Intertoobz, but I find my attention span has deteriorated. I always had a hard time wading through man pags and it's just gotten worse. Thank you very much.

---

