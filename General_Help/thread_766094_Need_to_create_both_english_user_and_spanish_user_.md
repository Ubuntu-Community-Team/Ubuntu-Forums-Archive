---
title: "Need to create both english user and spanish user profile on same computer"
date: 2008-04-25
forum: General Help
---

### Post by aprilloper on 2008-04-25
I am a computer operations adviser for a non-profit organization that runs seven preschools for low income children, many with Spanish-only speaking parents. Our preschools have one to two computers available for the parents of our students to use. Which are currently running Win2000 English, we would like to offer some Spanish language supported systems to give everyone fair and equal access to the resources we are offering.

I will be upgrading these computers soon and was wondering if it is possible to create two user profiles one English only and the other Spanish only? Or will I have to dual-boot a single computer 1st boot English, 2nd boot Spanish. Which is less desirable because I don't want to try and manage two separate installations. Additionally, I don't speak or read Spanish very well, so reading Spanish error messages would also be a problem.

I do have bilingual support staff at the schools that could help parents get started, but none of our staff are Linux users. I plan on having a very simple desktop, Firefox, OO Writer, OO Calc, OO Present, Exit/Log-off. Save to USB thumbdrive only. 

I have been searching for some kind of clue as to if my user profile option can be done. Which variant would be most likely to enable me to do this? I am leaning towards Ubuntu 7.10 or Edubuntu, however in my test lab Xubuntu seems to run the best on the recycled hardware I have available for the project. My hardware is Gateway 4200s, with 512 MB ram. 

Any help, suggestions, tips would be greatly appreciated.

---

### Post by elamericano on 2008-04-25
I decided to conduct this experiment with Ubuntu 8.04, and it's not perfect, but it works OK. A default language can be given to each user, but its pretty meaningless in Gnome. It only affects if you get a warning when you try to login with a different language than your default. If you then decide you want your default language you have to cancel the login, change the language manually, and re-login. Lame, huh?

Anyway, I expect it works the same way in 7.10, go to System->Administration->Login Support. Add Spanish + dialect (I used Mexico), then after installation it will be available for all users. You could make Spanish the default language, and then create a new user - this gives them folders with Spanish names (e.g. música), but it's not really necessary. In fact, you don't need a second user at all, if you don't want. Here's how it works:

At the login screen there is a button called Options, which allows you to change languages. You could select Spanish, then when you login all your menus, programs, and alert messages have Spanish text. If the login menu gets left in Spanish mode, you may need to know Opciónes, Seleccionar idioma, Inglés (E.E.U.U.), and Sí to get back to English. Any user can login with any of the available languages.

I'm sure these details are Gnome specific. Other Desktop Environments will be different, and I don't use them, so I don't know. KDE might be worth a look if it allows you to assign a language to a user, but the lighter weight DEs might have less support.

Oh, I almost forgot, right click on the top panel to add the "Keyboard Indicator". It will let you switch between USA and Esp keyboard layouts with a single click. Only a few keys are different with the traditional Spanish layout. The semicolon ; becomes ñ, the single quote (') followed by a letter will accent the letter así (use " for two marks, as on ü). + and _ are the question marks ¿?, ! is still !, but = is ¡. That's all you need.

Buena suerte.

---

