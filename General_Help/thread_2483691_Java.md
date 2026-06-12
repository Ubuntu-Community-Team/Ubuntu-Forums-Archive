---
title: "Java"
date: 2023-02-06
forum: General Help
---

### Post by lcabreram on 2023-02-06
How to move from version of JAVA on the terminal?

I install 3 different version of JAVA (8.18,19) and I want to know if I can move and use this different version inside the terminal of ubuntu

---

### Post by QIII on 2023-02-06
Moved to General Help.

Installation and Upgrades is specifically for the Ubuntu OS.

---

### Post by monkeybrain20122 on 2023-02-07
set up update-alternatives

[https://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk](https://askubuntu.com/questions/159575/how-do-i-make-java-default-to-a-manually-installed-jre-jdk)

If you installed all the javas from the repo the alternatives are already set up, you can switch between them either use cmd line

```
sudo update-alternatives --config java

```

It will show you the alternative versions available.

or use the galternatives gui (the second answer in link)

If you installed some versions of java manually (say you downloaded it from Oracle), then you have to add the alternative yourself. see first and the third answers.

---

### Post by ActionParsnip on 2023-02-07
Is space on the disk low? You can leave the other Javas and they'll cause no issues

---

### Post by Holger_Gehrke on 2023-02-07
Using 'update-alternatives' for switching between multiple versions of Java is a pain since each tool of a JRE or JDK is it's own group of alternatives. For that reason there's a specialized tool named update-java-alternatives which will switch all the alternatives. 'update-java-alternatives -l' will show you the installed alternatives with the name in the first column and 'update-java-alternatives -s java-name' will switch to a different java. 'update-java-alternatives' is part of the packages java-common which should be a dependency of all the various JREs and JDKs available from the repositories.

Holger

---

### Post by monkeybrain20122 on 2023-02-07
> **Holger_Gehrke said:**
> Using 'update-alternatives' for switching between multiple versions of Java is a pain since each tool of a JRE or JDK is it's own group of alternatives. For that reason there's a specialized tool named update-java-alternatives which will switch all the alternatives. 'update-java-alternatives -l' will show you the installed alternatives with the name in the first column and 'update-java-alternatives -s java-name' will switch to a different java. 'update-java-alternatives' is part of the packages java-common which should be a dependency of all the various JREs and JDKs available from the repositories.

Holger

Thanks for the info. I never have occasions to use different javas, I use update-alternatives for things like gcc and libblas. Good to know.

---

