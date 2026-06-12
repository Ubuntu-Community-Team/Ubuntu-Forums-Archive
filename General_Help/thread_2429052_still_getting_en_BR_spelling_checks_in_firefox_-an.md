---
title: "still getting en_BR spelling checks in firefox -and- incomplete language support"
date: 2019-10-12
forum: General Help
---

### Post by Skaperen on 2019-10-12
i am still getting en_BR spelling checks in firefox.  i should be getting en_US.  i have removed all packages i can find with "british" in the name.  yet this is still happening.  i have looked for references in [COLOR=#0000cd][FONT=courier new]**/etc**[/FONT][/COLOR] but find none (or don't know the right things to look for).  i recall encountering a case a few weeks ago of another application doing spelling checks with en_BR.  i have used right-click >> Add to Dictionary on many words like "color" so i don't see the red underlines for a en_US spelling.  does anyone know how to fix this?

i'm still getting that "_Incomplete Language Support_" pop up when i boot up and log in to admin.  i tracked that down as something missing for British language support.  it apparently thinks the system wants en_BR.  could this be something leaked into the distro by a Canonical developer?  where is the default system language specified?  can this be related to my firefox spelling check issue?

---

### Post by Artim on 2019-10-13
Perhaps this was done at installation time by mistake?  On my Xubuntu I installed Synaptic just so I could use the search feature for obscure stuff... perhaps a Synaptic search of "en_US" could be helpful, or a re-install of the language packages you want.

---

### Post by Skaperen on 2019-10-14
> **Artim said:**
> Perhaps this was done at installation time by mistake?  On my Xubuntu I installed Synaptic just so I could use the search feature for obscure stuff... perhaps a Synaptic search of "en_US" could be helpful, or a re-install of the language packages you want.

it usually defaults to US for the keyboard, so i have gotten into the habit of just pressing enter to get past it.  but if that was changed, that would be my mistake for not being observant.   i will do the reinstall of the language packages and see if that helps.  i did also install the packages for the Scandinavian languages.  i don't know if that could confuse anything.

---

### Post by Artim on 2019-10-14
Let us know if that works.  I am learning sign language, by the way.  Totally off-topic, but perhaps future editions of Xubuntu will offer it as an option! :lol:

---

### Post by Skaperen on 2019-10-14
there are websites that do.  i ran across some nice ones a few years ago.

---

### Post by Skaperen on 2019-10-15
sorry for the delayed reply.

yes, it does seem to have worked.  now i am getting squiggly red underlines on "colour" just as i would expect with an American dictionary in effect.

while doing that i saw packages for Australia, Canada, and South Africa.  i removed all of those to be sure.  there was also a generic (no language or country name shown) language package for firefox. it was among those that were re-installed.  everything with "English" in the name or description was reinstalled or if it had another country listed, was removed.  all the packages for Scandinavian languages were untouched (dictionaries).

---

