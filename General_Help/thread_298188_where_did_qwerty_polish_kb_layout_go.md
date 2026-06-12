---
title: "where did qwerty polish kb layout go?"
date: 2006-11-12
forum: General Help
---

### Post by mm201 on 2006-11-12
I have just switched to edgy and I cannot add a polish QWERTY keyboard layout.  The only polish keyboards available are the Dworak layouts and the QWERTZ.

Can anyone tell me how to add the QWERTY polish keyboard layout on edgy?

---

### Post by Bloch on 2007-04-29
I have just updated from Dapper Drake to Feisty, and have been trzing to get my old Polish keyboard. 
This is pretty crucial as I do  lot of Polish translations.

Does anyone have a suggestion for this?

---

### Post by zvacet on 2007-04-30
sysrem>settings>keyboard>select polish and chek it.Make it first on the list.You can unchek engish if you want.Did you download language suport?system>administration<language suport

---

### Post by Bloch on 2007-04-30
zvacet: The choice of the Polish qwerty keyboard is not there. I can choose the Polish qwertz keyboard but that is not what I want.

I am wondering if this is a recognised bug.

I notice the following post from Feb 3 2007 on the mint forum (mint is a derivative of ubuntu)
> I wanna report a bug there is no selection of Polish computer keyboard. To make so things clear:
- the most common (99.99% of computer users use it) layout is qwerty with the diacritic signs input as the combination of the key and the right ALT key, eg. ó = o + right ALT, &#322; = l + right ALT. This layout is missing Sad
- qwerzu used in old mechanical typewriters. Based on the German layout. I know only one user who uses this layout - an old professor, who "emulates" his typewriter with his laptop.
- Dvorak - I know no Polish user who uses it. Basically, it makes more problems than it solves. Represented in Mint three flavours Embarassed

I dare say that no one will miss any Dvorak layout. Everybody misses qwerty.

---

### Post by numer on 2007-05-16
Found it ! :cool:
It took a little digging, but I am not really that knowledgeable about X internals (definitely not as much as I would like to).
Anyway - the short of it is, setxkbmap needs to be invoked with -layout pl **-variant basic**, but for whatever reason that variant is not in the base.xml file anymore.  So I added it. :D

Remember to backup your base.xml file prior to making any changes!
The following section should be added to the /etc/X11/xkb/rules/base.xml file as a child of the <variantList> node that belongs to the <layout> node for layout 'pl'.  Search for <name>pl</name> to find the start tag for the <layout> element I am talking about.

```
        <variant>
          <configItem>
            <name>basic</name>
            <description>programmers</description>
            <description xml:lang="bg">programmers</description>
            <description xml:lang="en_GB">programmers</description>
            <description xml:lang="es">programmers</description>
            <description xml:lang="fi">programmers</description>
            <description xml:lang="fr">programmers</description>
            <description xml:lang="hu">programmers</description>
            <description xml:lang="it">programmers</description>
            <description xml:lang="ka">programmers</description>
            <description xml:lang="nl">programmers</description>
            <description xml:lang="ru">programmers</description>
            <description xml:lang="sl">programmers</description>
            <description xml:lang="sr">programmers</description>
            <description xml:lang="sr@Latn">programmers</description>
            <description xml:lang="sv">programmers</description>
            <description xml:lang="tr">programmers</description>
            <description xml:lang="uk">programmers</description>
            <description xml:lang="vi">programmers</description>
            <description xml:lang="zh_TW">programmers</description>
          </configItem>
        </variant>
```

Save the file and restart X (not sure if that is really necessary).  You should see a choice for 'programmers' variant on the list of variants for layout 'pl' now.  Jak wida&#263; na przyk&#322;adzie, to dzia&#322;a!

Now if I only knew how to submit that modification to whoever is maintaining this.

---

### Post by joninkrakow on 2007-07-10
Actually, I'm interested in a variant of the QWERTZ "maszynistka" keyboard layout that I've used for years on my Macs. On this variant, the &#347;,&#324; and &#263; are on the bottom row. next to the m key, but accessed with the <shift>, and ó and &#378; are next to the p. Is this something unique to the Mac? This was the default layout on my Duo when I bought it, and what got me started using it in the first place. Now I can't type Polish without it! (&#322;, &#261; and &#281; don't move, but all the rest do--&#380; is next to the zero key)

-Jon

---

