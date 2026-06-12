---
title: "How to sed -i ?"
date: 2015-12-03
forum: General Help
---

### Post by fairbird on 2015-12-03
Hi guys ...

I want to replace some line in one of file with sed command ..
But i got error ...

Original line is:
```
'/share/enigma2/skin_default/spinner/'
```
I want to change it to this line:
```
'/share/enigma2/spinner/'
```

I've use this command but I have got error
```
sed -i 's/'/share/enigma2/skin_default/spinner'/'/share/enigma2/spinner/'g' /tmp/1
```

I got this error
```
sed: bad option in substitution expression
```

Any one can fix command to correct one ?!

Thank you Advanced

---

### Post by matt_symes on 2015-12-03
Hi

Here is a quick temporary file

```

matthew-xu-16-04:/home/matthew:4 % cat tmp
/share/enigma2/skin_default/spinner
matthew-xu-16-04:/home/matthew:4 
```

To change it to /share/enigma2/spinner, you need to escape the forward slashes with back slashes. This is sometimes called picket fencing.

```
matthew-xu-16-04:/home/matthew:4 % sed  's/\/share\/enigma2\/skin_default\/spinner/\/share\/enigma2\/spinner/g' tmp
/share/enigma2/spinner
matthew-xu-16-04:/home/matthew:4 
```

You can also choose a different character to be the separator in sed. In this example I'm using the = sign.
```

matthew-xu-16-04:/home/matthew:4 % sed  's=/share/enigma2/skin_default/spinner=/share/enigma2/spinner=g' tmp       
/share/enigma2/spinner
matthew-xu-16-04:/home/matthew:4 % 
```

EDIT:

I'm also going to move this thread to **General Help.**

Kind regards

---

### Post by fairbird on 2015-12-03
Thank you ..
Really helpful

Solved ...

---

