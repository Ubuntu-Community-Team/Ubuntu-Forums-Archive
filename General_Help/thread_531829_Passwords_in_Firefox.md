---
title: "Passwords in Firefox"
date: 2007-08-22
forum: General Help
---

### Post by ramjet_1953 on 2007-08-22
I have three Yahoo mail accounts an have noticed that Firefox doesn't see the login and password exchange.

Hence it doesn't offer me the option to save the passwords.

This works perfectly in Opera.

Are there any work-arounds?

Regards,
Roger :cool:

---

### Post by kerry_s on 2007-08-22
use a remember password bookmarklet.
```
javascript:(function(){var ca,cea,cs,df,dfe,i,j,x,y;function n(i,what){return i+%22 %22+what+((i==1)?%22%22:%22s%22)}ca=cea=cs=0;df=document.forms;for(i=0;i<df.length;++i){x=df[i];dfe=x.elements;if(x.onsubmit){x.onsubmit=%22%22;++cs;}if(x.attributes[%22autocomplete%22]){x.attributes[%22autocomplete%22].value=%22on%22;++ca;}for(j=0;j<dfe.length;++j){y=dfe[j];if(y.attributes[%22autocomplete%22]){y.attributes[%22autocomplete%22].value=%22on%22;++cea;}}}alert(%22Removed autocomplete=off from %22+n(ca,%22form%22)+%22 and from %22+n(cea,%22form element%22)+%22, and removed onsubmit from %22+n(cs,%22form%22)+%22. After you type your password and submit the form, the browser will offer to remember your password.%22)})();
```

you click on it before you login and it will ask to remember.

---

### Post by ramjet_1953 on 2007-08-22
Thaks for that kerry_s.

Much appreciated.

I want to change over to FireFox, as I'm having some rendering problems with Opera.

Regards,
Roger :cool:

---

### Post by ramjet_1953 on 2007-08-22
Thanks again, kerry_s, it worked a treat!

Perhaps this method should be included in the Ubuntu Guide?

I'm sure lots of people would find it helpful.

Regards,
Roger 8)

---

