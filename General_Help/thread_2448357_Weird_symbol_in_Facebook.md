---
title: "Weird symbol in Facebook"
date: 2020-08-06
forum: General Help
---

### Post by sbennettgso on 2020-08-06
This might seem to be a weird question to ask here... I use a Chrome app for Facebook, and occasionally I see a post that has this symbol in it, a crook with a dot as in the screenshot below:

[IMG]https://scontent-iad3-1.xx.fbcdn.net/v/t1.0-9/117115879_3287520381306783_8081327971397052418_n.jpg?_nc_cat=101&_nc_sid=1480c5&_nc_ohc=Kbnmdp3aE8oAX8ZixHy&_nc_ht=scontent-iad3-1.xx&oh=9aa7091d3dda70e55e8dc8c63517cee5&oe=5F522299[/IMG]

I only seem to see it when using this app on my Ubuntu Budgie 20.04 machine.  Any ideas?

---

### Post by sdsurfer on 2020-08-06
There's a lot to this answer, will try to simplify it . . . it has to do with the encoding of the web page text and how your browser is interpreting it. So even though you see it in one condition, it will have to do with that browser and the fonts enabled on your system. 

I couldn't find a Unicode representation of this symbol (I **think** it is from ancient Egyptian, a crook and flail.) For other browsers it will probably look like a small square in place of the character with 1's and 0's in it, because the browser can't interpret the symbol.

This is further complicated by the fonts installed on your system and the web page importing the fonts it needs. If the font is not available, it will not render. A good example is, in my Firefox under Ubuntu I cannot see any of the symbols in the left column here.

[https://en.wikipedia.org/wiki/List_of_Egyptian_hieroglyphs](https://en.wikipedia.org/wiki/List_of_Egyptian_hieroglyphs)

What do you see when you look at the same content in other browsers? Right-click the text itself and select "inspect element," show us what Unicode character it is using.

---

