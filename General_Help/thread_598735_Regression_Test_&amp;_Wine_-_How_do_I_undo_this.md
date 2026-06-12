---
title: "Regression Test &amp; Wine - How do I undo this"
date: 2007-10-31
forum: General Help
---

### Post by mylemonblue on 2007-10-31
In these last three weeks of using Ubuntu for the first time I've managed completely on my own but this one got me. Thank you for any help you can give. 

I posted a bug report at WineHQ. A gentleman replying to it said I need to run the [[color=blue]Regression Test[/color]]("http://wiki.winehq.org/RegressionTesting"). Having done so has moved my original ".wine" directory filled with programs I use daily to ".wine-backup" rendering them unusable. The test created a new one in it's place. All the normal command lines for Wine only refer to that new installation now. Neither he nor the Regression Test instructions addressed this or how I'm to revert things back to my original Wine installation as it was before the test changed it.  I'm kind of stuck now. #-o

Does anyone know how to return my original Wine installation to it's original condition? Is there a proper way to do this without breaking something?
[COLOR="DimGray"](I'm also afraid of any configuration files that might be involved in places I may be unaware of)[/COLOR]



Edit to add " may be" to the last line.

---

### Post by emwine on 2007-10-31
> Does anyone know how to return my original Wine installation to it's original condition? Is there a proper way to do this without breaking something?
You just restore your .wine-backup back to ~/.wine.  Make sure the current ~/.wine is indeed the regression test one, then:```
rm -rf .wine
```
And then:```
mv ~/.wine-backup ~/.wine
```

It's probably safer in the long run to use a prefix for either your main wine directory or for your testing directory.  That way you don't have to be moving those directories around.  I lost an important one that way somehow years ago-- I won't do that again.

---

### Post by mylemonblue on 2007-10-31
> **emwine said:**
> You just restore your .wine-backup back to ~/.wine.  Make sure the current ~/.wine is indeed the regression test one, then:```
rm -rf .wine
```
And then:```
mv ~/.wine-backup ~/.wine
```

It's probably safer in the long run to use a prefix for either your main wine directory or for your testing directory.  That way you don't have to be moving those directories around.  I lost an important one that way somehow years ago-- I won't do that again.


I was thinking it might be that simple but I thought it would be best to ask before taking another blind leap like I did with that regression test. I was affraid doing this could mess up something in apt-get somewhere that I might not be aware of. For all I've learned I've got a long ways to go. LOL.

Thank you so much.


Edit to add. I was leaning toward using.  
```
apt-get --purge remove <package>
```
I know enough to really get myself in trouble. LOL.

---

