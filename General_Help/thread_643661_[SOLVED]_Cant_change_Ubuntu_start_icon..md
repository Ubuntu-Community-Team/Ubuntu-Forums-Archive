---
title: "[SOLVED] Cant change Ubuntu start icon."
date: 2007-12-18
forum: General Help
---

### Post by BluePlum on 2007-12-18
Hey,  look at my screenshot below. I go to change my start icon, I go into apps/panal/objects/( were my start button is ) i select use custom icon. Then when i try to change the text it wont let me. ( look at screenshot ) any Suggestion?

---

### Post by BluePlum on 2007-12-18
any1?

---

### Post by tich on 2007-12-18
i wish i had suggestions but i don't... i have been trying to figure that out for a long time now!  hopefully someone will post an answer!

---

### Post by BluePlum on 2007-12-18
I think it has something to do with us not having permision... but im proboly 100% rong,,,

---

### Post by BluePlum on 2007-12-19
o yer any1 no how to do it?:lolflag:

---

### Post by bionnaki on 2007-12-19
search for distributor-logo.png and replace that image with your image of choice. and then log out.

---

### Post by BluePlum on 2007-12-19
Were can i find that picture? were is it located?

---

### Post by danwood76 on 2007-12-19
/usr/share/icons/

Its in various locations within that folder depending on reolution of icon and theme.

for example /usr/share/icons/Human/24x24/places/distributor-logo.png is the default gutsy panel icon, 24x24 is the default icon size I think.

---

### Post by chrisccoulson on 2007-12-19
> **BluePlum said:**
> Hey,  look at my screenshot below. I go to change my start icon, I go into apps/panal/objects/( were my start button is ) i select use custom icon. Then when i try to change the text it wont let me. ( look at screenshot ) any Suggestion?

I think you might be confused. The key you are looking at is a boolean, which you can only set to true or false to tell the menu bar whether to use a custom icon or not. This key doesn't contain the location of that icon. The text in your screenshot is the name of the key (not a value), which you cannot change. To specify the location of your icon, you need to navigate to the '/apps/panel/object/object_1/custom_icon' key (which is a string) and specify the location of the file here (as well as setting 'use_custom_icon' to true)

Edit: I've just realised that changing these keys won't give you the effect you desire anyway. You need a distributor-logo icon as part of your icon theme (as someone has already pointed out).

---

