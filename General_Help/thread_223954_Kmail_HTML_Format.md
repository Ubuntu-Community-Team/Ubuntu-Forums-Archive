---
title: "Kmail HTML Format"
date: 2006-07-27
forum: General Help
---

### Post by wizzkid on 2006-07-27
Hi I received an email from my friend. When I replier it and I make my reply in bold letter or has a color on it, the quoted message (email of my friend, just below my email) became in double space. 

Is there a way to make it in single space even I used HTML in my reply?

Thanks a lot.

Pleae advice,

---

### Post by asimon on 2006-07-27
Yes, you're right. I was able to reproduce this problem. It seems kmail wraps every single line into <p></p> tags. Seems to be a bug.  

Kmail's html support when composing messages is not very good and the generated html code is very very ugly. There are already several bugs filed about this in KDE's bug tracking system. But I suppose there won't be any big changes to kmail's html support before KDE 4.

---

### Post by wizzkid on 2006-07-27
Hi Asimon,

Thank you so much for your response to this issue, Truely appreciate your effort for this matter.

---

