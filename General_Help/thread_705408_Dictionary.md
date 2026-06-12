---
title: "Dictionary"
date: 2008-02-23
forum: General Help
---

### Post by ronb94 on 2008-02-23
Hello
1 of the thing that I'm really missing in ubuntu is Dictionary.
Photoshop I can run with wine, and for games I dual boot so I make my XP just for games.
But if I want to translate something I have reboot to my xp or running a virtual xp.
The gnome dictionary is not good because I need all those languages:
Hebrew
Russian
English
French 
I searched a lot for a good dictionary but I didn't find nothing.
Is there a good dictionary for ubuntu with all those languages I need?
Thanks

---

### Post by StOoZ on 2008-02-23
you can use stardict..
its pretty good, and you can convert the babylon dics to the stardict types easily
just google about it.

---

### Post by ronb94 on 2008-02-23
Thanks i'll try it but how do I convert the babylon dics to the stardict?

---

### Post by y-lee on 2008-02-23
> **ronb94 said:**
> The gnome dictionary is not good because I need all those languages:
Hebrew
Russian
English
French 
I searched a lot for a good dictionary but I didn't find nothing.
Is there a good dictionary for ubuntu with all those languages I need?
Thanks


Hello

I'm not sure what you want here, a dictionary to define words in one language or a dictionary to translate words. But the Gnome Dictionary is a [DICT Client]("http://en.wikipedia.org/wiki/DICT_client") which can handle different dictionaries. By default it comes with  English, French  and Spanish. To see open the Dictionary, click **Edit** and then **Preferences**, you should see

[LIST]
[*]Default Dictionary Server
[*]French Dictionaries from Wikipedia
[*]Spanish  Dictionary
[/LIST]

Simply click one to change it.

To add Dictionaries it helps to have installed the dict package.

```
sudo apt-get install dict
```

Now to see available a list of online databases at dict.org:

```
dict -h dict.org --dbs
```

The result I got from this was

```
Databases available:
 gcide      The Collaborative International Dictionary of English v.0.48
 wn         WordNet (r) 2.0
 moby-thes  Moby Thesaurus II by Grady Ward, 1.0
 elements   Elements database 20001107
 vera       Virtual Entity of Relevant Acronyms (Version 1.9, June 2002)
 jargon     Jargon File (4.3.1, 29 Jun 2001)
 foldoc     The Free On-line Dictionary of Computing (27 SEP 03)
 easton     Easton's 1897 Bible Dictionary
 hitchcock  Hitchcock's Bible Names Dictionary (late 1800's)
 bouvier    Bouvier's Law Dictionary, Revised 6th Ed (1856)
 devils     THE DEVIL'S DICTIONARY ((C)1911 Released April 15 1993)
 world02    CIA World Factbook 2002
 gazetteer  U.S. Gazetteer (1990)
 gaz-county U.S. Gazetteer Counties (2000)
 gaz-place  U.S. Gazetteer Places (2000)
 gaz-zip    U.S. Gazetteer Zip Code Tabulation Areas (2000)
 --exit--   Stop default search here.
 afr-deu    Africaan-German Freedict dictionary
 afr-eng    Africaan-English Freedict Dictionary
 ara-eng    English-Arabic Freedict Dictionary
 cro-eng    Croatian-English Freedict Dictionary
 cze-eng    Czech-English Freedict dictionary
 dan-eng    Danish-English Freedict dictionary
 deu-eng    German-English Freedict dictionary
 deu-fra    German-French Freedict dictionary
 deu-ita    German-Italian Freedict dictionary
 deu-nld    German-Nederland Freedict dictionary
 deu-por    German-Portugese Freedict dictionary
 eng-afr    English-Africaan Freedict Dictionary
 eng-ara    English-Arabic FreeDict Dictionary
 eng-cro    English-Croatian Freedict Dictionary
 eng-cze    English-Czech fdicts/FreeDict Dictionary
 eng-deu    English-German Freedict dictionary
 eng-fra    English-French Freedict Dictionary
 eng-hin    English-Hindi Freedict Dictionary
 eng-hun    English-Hungarian Freedict Dictionary
 eng-iri    English-Irish Freedict dictionary
 eng-ita    English-Italian Freedict dictionary
 eng-lat    English-Latin Freedict dictionary
 eng-nld    English-Netherlands Freedict dictionary
 eng-por    English-Portugese Freedict dictionary
 eng-rom    English-Romanian FreeDict dictionary
 eng-rus    English-Russian Freedict dictionary
 eng-spa    English-Spanish Freedict dictionary
 eng-swa    English-Swahili xFried/FreeDict Dictionary
 eng-swe    English-Swedish Freedict dictionary
 eng-tur    English-Turkish FreeDict Dictionary
 eng-wel    English-Welsh Freedict dictionary
 fra-deu    French-German Freedict dictionary
 fra-eng    French-English Freedict dictionary
 fra-nld    French-Nederlands Freedict dictionary
 hin-eng    English-Hindi Freedict Dictionary [reverse index]
 hun-eng    Hungarian-English FreeDict Dictionary
 iri-eng    Irish-English Freedict dictionary
 ita-deu    Italian-German Freedict dictionary
 jpn-deu    Japanese-German Freedict dictionary
 kha-deu    Khasi-German FreeDict Dictionary
 lat-deu    Latin-German Freedict dictionary
 lat-eng    Latin-English Freedict dictionary
 nld-deu    Nederlands-German Freedict dictionary
 nld-eng    Nederlands-English Freedict dictionary
 nld-fra    Nederlands-French Freedict dictionary
 por-deu    Portugese-German Freedict dictionary
 por-eng    Portugese-English Freedict dictionary
 sco-deu    Scottish-German Freedict dictionary
 scr-eng    Serbo-Croat-English Freedict dictionary
 slo-eng    Slovenian-English Freedict dictionary
 spa-eng    Spanish-English Freedict dictionary
 swa-eng    Swahili-English xFried/FreeDict Dictionary
 swe-eng    Swedish-English Freedict dictionary
 tur-deu    Turkish-German Freedict dictionary
 tur-eng    Turkish-English Freedict dictionary
 english    English Monolingual Dictionaries
 trans      Translating Dictionaries
 all        All Dictionaries (English-Only and Translating)
 web1913    Webster's Revised Unabridged Dictionary (1913)
 world95    The CIA World Factbook (1995)

```

So to add say the English-Russian Freedict dictionary open the gnome dictionary click **Edit** and the **Preferences** and then the **Add **button on the Source page. In** Description** put *English-Russian Freedict dictionary* (or whatever you want). Now double click The **Transport** button to be sure it says *Dictionary Server* and when you do this it should expand to show **Hostname** and **Port**. These should already be filled in and say **Hostname**: dict.org and **Port:** 2628.

Now click **Advanced settings**, put *eng-rus* in the **Database** text box and finish by clicking **Add**. Now select the dictionary you just added. Test it by trying a word. You can do the same with any of the dictionary databases at **dict.org.**

[CENTER][IMG]http://www.fileden.com/files/2006/11/26/425005/add.png[/IMG]

[IMG]http://www.fileden.com/files/2006/11/26/425005/Images/Ubuntu/translate.png[/IMG][/CENTER]

Now I didn't see a Hebrew to English dictionary in the list but there are other [DICT protocol servers]("http://luetzschena-stahmeln.de/dictd/index.php"). To see what is on one for example, dict://vocabulary.aioe.org, use

```
dict -h vocabulary.aioe.org --dbs
```

In this case I got 

```
Databases available:
 gcide            The Collaborative International Dictionary of English v.0.48
 wn               WordNet (r) 2.0 (August 2003)
 foldoc           The Free On-line Dictionary of Computing (19 Sep 2003)
 jargon           Jargon File (4.4.4, 14 Aug 2003)
 vera             V.E.R.A. -- Virtual Entity of Relevant Acronyms (December 2003)
 devil            The Devil's Dictionary (1881-1906)
 elements         The Elements (07Nov00)
 easton           Easton's 1897 Bible Dictionary
 hitchcock        Hitchcock's Bible Names Dictionary (late 1800's)
 gaz              U.S. Gazetteer (1990)
 1000pbio         1000+ biography
 abr1w            &#1057;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1089;&#1080;&#1085;&#1086;&#1085;&#1080;&#1084;&#1086;&#1074; &#1053;.&#1040;&#1073;&#1088;&#1072;&#1084;&#1086;&#1074;&#1072;
 afr-deu          Africaan-German Freedict dictionary
 afr-eng          afr-eng
 ahiezer          &#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1099; &#1082;&#1085;&#1080;&#1075;&#1080; «&#1050;&#1088;&#1080;&#1090;&#1080;&#1082;&#1072; &#1080;&#1089;&#1090;&#1086;&#1088;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1075;&#1086; &#1086;&#1087;&#1099;&#1090;&#1072;» &#1040;.&#1057;.&#1040;&#1093;&#1080;&#1077;&#1079;&#1077;&#1088;&#1072;
 anhviet109K      @00-database-short
 ati              Glosario ATI
 aviation         Russian abbreviations for aviation
 beslov           &#1041;&#1086;&#1083;&#1100;&#1096;&#1086;&#1081; &#1069;&#1085;&#1094;&#1080;&#1082;&#1083;&#1086;&#1087;&#1077;&#1076;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1057;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 biology          biology
 bouvier          Bouvier's Law Dictionary, Revised 6th Ed (1856)
 brok_and_efr     &#1069;&#1085;&#1094;&#1080;&#1082;&#1083;&#1086;&#1087;&#1077;&#1076;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1041;&#1088;&#1086;&#1082;&#1075;&#1072;&#1091;&#1079;&#1072; &#1080; &#1045;&#1092;&#1088;&#1086;&#1085;&#1072;
 church           &#1057;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1094;&#1077;&#1088;&#1082;&#1086;&#1074;&#1085;&#1099;&#1093; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1086;&#1074;
 littre           XMLittré (1877)
 cro-eng          Croatian-English Freedict Dictionary
 cze-eng          Czech-English Freedict dictionary
 dalf             &#1058;&#1086;&#1083;&#1082;&#1086;&#1074;&#1099;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1078;&#1080;&#1074;&#1086;&#1075;&#1086; &#1074;&#1077;&#1083;&#1080;&#1082;&#1086;&#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1075;&#1086; &#1103;&#1079;&#1099;&#1082;&#1072;
 dan-eng          Danish-English Freedict dictionary
 debian.bg-en     &#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1086; - &#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080; &#1088;&#1077;&#1095;&#1085;&#1080;&#1082; &#1085;&#1072; &#1044;&#1077;&#1073;&#1080;&#1072;&#1085;
 debian.de-en     Debian Wörterbuch Deutsch-Englisch
 debian.en-bg     &#1040;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1086; - &#1073;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080; &#1088;&#1077;&#1095;&#1085;&#1080;&#1082; &#1085;&#1072; &#1044;&#1077;&#1073;&#1080;&#1072;&#1085;
 debian.en-de     Debian Wörterbuch Englisch-Deutsch
 debian.en-es     Diccionario Inglés-Español de Debian
 debian.en-fi     Dictionary Englsh - Finnish
 debian.en-fr     Petit lexique anglais-français de termes et abbréviations  Debian
 debian.en-lt     Dictionary en - lt
 debian.en-nl     Debian Dictionaire English-Nederlands
 debian.en-pa     Debian Dictionary English-Punjabi
 debian.en-pl     Debian S&#322;ownik angielsko-polski
 debian.en-pt     Dicionário Debian Inglês-Português
 debian.en-vi     T&#7915; &#273;i&#7875;n Anh-Vi&#7879;t
 debian.es-en     Diccionario Español-Inglés de Debian
 debian.fi-en     Dictionary Finnish - English
 debian.fr-en     Petit lexique français-anglais de termes et abbréviations  Debian
 debian-glossary.bg &#1056;&#1077;&#1095;&#1085;&#1080;&#1082; &#1085;&#1072; Debian &#1080; &#1089;&#1087;&#1080;&#1089;&#1098;&#1082; &#1085;&#1072; &#1089;&#1098;&#1082;&#1088;&#1072;&#1097;&#1077;&#1085;&#1080;&#1103;&#1090;&#1072;
 debian-glossary.de Debian Wörterbuch und Abkürzungsverzeichnis
 debian-glossary.en Debian Dictionary and List of Acronyms
 debian-glossary.es Diccionario y lista de acrónimos de Debian
 debian-glossary.fi Debian Dictionary and List of Acronyms
 debian-glossary.fr Petit lexique de termes et d'abbréviations Debian
 debian-glossary.lt Debian'o &#382;odynas ir akronim&#371; s&#261;ra&#353;as
 debian-glossary.nl Debian Dictionary and List of Acronyms
 debian-glossary.pa &#2593;&#2632;&#2604;&#2624;&#2565;&#2600; &#2614;&#2604;&#2598;-&#2581;&#2635;&#2614; &#2596;&#2631; Acronyms &#2616;&#2626;&#2586;&#2624;
 debian-glossary.pl S&#322;ownik
 debian-glossary.pt Dicionário Debian e Lista de Acrônimos
 debian-glossary.vi T&#7915; &#273;i&#7875;n và Danh sách T&#7915; c&#7845;u t&#7841;o Debian
 debian.lt-en     Dictionary lt - en
 debian.nl-en     Debian Dictionaire Nederlands-English
 debian.pa-en     Debian Dictionary Punjabi-English
 debian.pl-en     Debian S&#322;ownik polsko-angielski
 debian.pt-en     Dicionário Debian Português-Inglês
 debian.vi-en     T&#7915; &#273;i&#7875;n Vi&#7879;t-Anh
 deu-eng          German-English Freedict dictionary
 deu-fra          German-French Freedict dictionary
 deu-ita          German-Italian Freedict dictionary
 deu-nld          German-Nederland Freedict dictionary
 deu-por          German-Portugese Freedict dictionary
 deutsch_de-ru    Deutsch-Russian dictionary
 deutsch_ru-de    Russian-Deutsch dictionary
 dv45K            @00-database-short
 dward.bg         &#1057;&#1087;&#1088;&#1072;&#1074;&#1086;&#1095;&#1077;&#1085; &#1092;&#1072;&#1081;&#1083; &#1089;&#1098;&#1089; &#1089;&#1098;&#1082;&#1088;&#1072;&#1097;&#1077;&#1085;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1078;&#1077;&#1085;&#1080;&#1090;&#1077; &#1074; Debian
 dward.de         Debian Abkürzungs-Referenz-Wörterterbuch
 dward.en         Debian Acronym Reference Dictionary
 dward.es         Debian Acronym Reference Dictionary
 dward.fi         Debian Acronym Reference Dictionary
 dward.fr         Petit lexique de termes et d'abbréviations Debian
 dward.lt         Debian'o Moter&#371; akronim&#371; nuorod&#371; &#382;odynas
 dward.nl         Debian Acronym Reference Dictionary
 dward.pa         Debian Acronym Reference Dictionary
 dward.pl         Akronimy
 dward.pt         Dicionário de Referência de Acrônimos
 dward.vi         T&#7915; &#273;i&#7875;n Tham chi&#7871;u T&#7915; c&#7845;u t&#7841;o Ph&#7909; n&#7919; Debian
 e2i              e2i Spanish-to-English Dictionary
 eng-afr          eng-afr
 eng-ara          English-Arabic FreeDict Dictionary
 eng-cro          English-Croatian Freedict Dictionary
 eng-cze          English-Czech fdicts/FreeDict Dictionary
 eng-deu          English-German Freedict dictionary
 eng-fra          eng-fra
 eng-hin          English-Hindi Freedict Dictionary
 eng-hun          eng-hun
 eng-iri          English-Irish Freedict dictionary
 eng-ita          English-Italian Freedict dictionary
 eng-lat          English-Latin Freedict dictionary
 english-german   English - German Dictionary 1.3
 eng-nld          English-Netherlands Freedict dictionary
 eng-por          English-Portugese Freedict dictionary
 eng-rom          English-Romanian FreeDict dictionary
 eng-rus          English-Russian Freedict dictionary
 eng-spa          English-Spanish Freedict dictionary
 eng-swa          English-Swahili xFried/FreeDict Dictionary
 eng-swe          English-Swedish Freedict dictionary
 eng-tur          English-Turkish FreeDict Dictionary
 eng-wel          English-Welsh Freedict dictionary
 es-de            Diccionario Espanol-Aleman
 esp-spa          Diccionario spa-esp de Esperanto a Castellano
 ethnographic     &#1069;&#1090;&#1085;&#1086;&#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 findict          &#1057;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1092;&#1080;&#1085;&#1072;&#1085;&#1089;&#1086;&#1074;&#1099;&#1093; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1086;&#1074;
 fra-deu          French-German Freedict dictionary
 fra-eng          French-English Freedict dictionary
 fra-nld          French-Nederlands Freedict dictionary
 gaz2k-counties   U.S. Gazetteer Counties (2000)
 gaz2k-places     U.S. Gazetteer Places (2000)
 gaz2k-zips       U.S. Gazetteer Zip Code Tabulation Areas (2000)
 comn_sdict_axm03_Hebrew_romanized_English comn_sdict_axm03_Hebrew_romanized_English
 geology_ru-en    Geological Russian-English dictionary
 german-english   German - English Dictionary 1.3
 giait            GIAIT: Diccionario Informatico Ingles-Castellano
 hi127            &#1057;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;-&#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1077;&#1083;&#1100; &#1087;&#1086; &#1076;&#1088;&#1077;&#1074;&#1085;&#1077;&#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1084;&#1091; &#1080;&#1089;&#1082;&#1091;&#1089;&#1089;&#1090;&#1074;&#1091;
 hun-eng          Hungarian-English FreeDict Dictionary
 i2e              i2e English-to-Spanish Dictionary
 idioms           &#1056;&#1091;&#1089;&#1089;&#1082;&#1086;-&#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1080;&#1076;&#1080;&#1086;&#1084;
 iri-eng          Irish-English Freedict dictionary
 ita-deu          Italian-German Freedict dictionary
 kernelnewbies-es Kernelnewbies en espanol
 komi-rus         Komi-Russian Dictionary
 korolew_ru-en    korolew_ru-en
 lat-deu          Latin-German Freedict dictionary
 lat-eng          Latin-English Freedict dictionary
 latrus           &#1051;&#1072;&#1090;&#1080;&#1085;&#1089;&#1082;&#1086;-&#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 magus            &#1053;&#1086;&#1074;&#1099;&#1081; &#1041;&#1086;&#1083;&#1100;&#1096;&#1086;&#1081; &#1072;&#1085;&#1075;&#1083;&#1086;-&#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 mech             mech
 meddict          &#1052;&#1077;&#1076;&#1080;&#1094;&#1080;&#1085;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 moby-thesaurus   Moby Thesaurus II by Grady Ward, 1.0
 muiswerk         Dutch monolingual dictionary
 ngaviet          @00-database-short
 nld-deu          Nederlands-German Freedict dictionary
 nld-eng          Nederlands-English Freedict dictionary
 nld-fra          Nederlands-French Freedict dictionary
 nv20K            nv20K
 ozhegov          &#1058;&#1086;&#1083;&#1082;&#1086;&#1074;&#1099;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1054;&#1078;&#1077;&#1075;&#1086;&#1074;&#1072;
 ozhshv           &#1058;&#1086;&#1083;&#1082;&#1086;&#1074;&#1099;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1075;&#1086; &#1103;&#1079;&#1099;&#1082;&#1072; &#1054;&#1078;&#1077;&#1075;&#1086;&#1074;&#1072; &#1080; &#1064;&#1074;&#1077;&#1076;&#1086;&#1074;&#1086;&#1081;
 phapviet         @00-database-short
 por-deu          Portugese-German Freedict dictionary
 por-eng          Portugese-English Freedict dictionary
 religion         Religion
 sco-deu          Scottish-German Freedict dictionary
 scr-eng          Serbo-Croat-English Freedict dictionary
 sinyagin_abbrev  sinyagin_abbrev
 sinyagin_business sinyagin_business
 sinyagin_general_er sinyagin_general_er
 sinyagin_general_re sinyagin_general_re
 slo-eng          Slovenian-English Freedict dictionary
 slovnyk_be-en    slovnyk_be-en
 slovnyk_be-pl    slovnyk_be-pl
 slovnyk_be-ru    slovnyk_be-ru
 slovnyk_be-uk    slovnyk_be-uk
 slovnyk_pl-be    slovnyk_pl-be
 slovnyk_pl-en    slovnyk_pl-en
 slovnyk_pl-ru    slovnyk_pl-ru
 slovnyk_pl-uk    slovnyk_pl-uk
 slovnyk_ru-be    slovnyk_ru-be
 slovnyk_ru-en    slovnyk_ru-en
 slovnyk_ru-pl    slovnyk_ru-pl
 slovnyk_ru-uk    slovnyk_ru-uk
 slovnyk_uk-be    slovnyk_uk-be
 sl-urjc          Sofware Libre URJC
 spa-eng          Spanish-English Freedict dictionary
 spa-esp          Diccionario esp-spa de Castellano a Esperanto
 swa-eng          Swahili-English xFried/FreeDict Dictionary
 swe-eng          Swedish-English Freedict dictionary
 tur-deu          Turkish-German Freedict dictionary
 tur-eng          Turkish-English Freedict dictionary
 unix-man         L4(8)
 vd12K            @00-database-short
 vietanh          @00-database-short
 vietphap         @00-database-short
 www              WHO WAS WHO 5000 B. C. to Date
 Geodic           Geodic
 alex-cc          Alex - Codice Civile
 alex-cds         Alex - Codice della strada
 alex-cpc         Alex - Codice di Procedura Civile
 alex-cp          Alex - Codice Penale
 alex-cpp         Alex - Codice di Procedura Penale
 ediclsd4         ediclsd4
 enamdict         enamdict
 engscidic        engscidic
 en-ru-bars       en-ru-bars
 findic           findic
 foguangdacidian  foguangdacidian
 forsdic_s        forsdic_s
 gaojihanyudacidian gaojihanyudacidian
 guojibiaozhunhanzidacidian guojibiaozhunhanzidacidian
 handedict-gb     handedict-gb
 hanzim           hanzim
 JCEDict          JCEDict
 jmdict-en-ja     jmdict-en-ja
 jmdict-ja-en     jmdict-ja-en
 jplaces          jplaces
 kanjidic2        kanjidic2
 oald             oald
 pc-user-ru       pc-user-ru
 quick_ryska-svenska quick_ryska-svenska
 quick_spa-dan    quick_spa-dan
 quick_spanish-english quick_spanish-english
 quick_svenska-spanska quick_svenska-spanska
 quick_walesiska-svenska quick_walesiska-svenska
 riverwater       riverwater
 sanzunfasu-gb    sanzunfasu-gb
 sanzunfasu       sanzunfasu
 soothill-buddhist-gb soothill-buddhist-gb
 stardict         stardict
 wadokujt         wadokujt
 xdict-ec-big5    xdict-ec-big5
 xdict-ec-gb      xdict-ec-gb
 slovnyk_uk-en    slovnyk_uk-en
 slovnyk_uk-pl    slovnyk_uk-pl
 slovnyk_uk-ru    slovnyk_uk-ru
 sokrat_en-ru     sokrat_enru
 sokrat_ru-en     sokrat_ruen
 swedish_ru-sv    Russian-Swedish dictionary
 swedish_sv-ru    Swedish-Russian dictionary
 teo              &#1058;&#1077;&#1086;&#1089;&#1086;&#1092;&#1089;&#1082;&#1080;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100;
 ushakov          &#1058;&#1086;&#1083;&#1082;&#1086;&#1074;&#1099;&#1081; &#1089;&#1083;&#1086;&#1074;&#1072;&#1088;&#1100; &#1059;&#1096;&#1072;&#1082;&#1086;&#1074;&#1072;
 zhelezyaki_abbr  USSR abbreviations for chips
 zhelezyaki_analogs Analogs for USSR chips

```

Note: some of these characters above may not be not showing up  right, they should in your terminal tho ;)

To add one of these it is the same precedure as above with the exception we must change Hostname from dict.org to vocabulary.aioe.org.

So if you look around you should be able to find the dictionaries you need for the gnome dicionary. :)

---

### Post by y-lee on 2008-02-23
> **ronb94 said:**
> Thanks i'll try it but how do I convert the babylon dics to the stardict?

:lolflag: my last post took a while 


[LIST]
[*][StarDict]("http://stardict.sourceforge.net/"). this is I think in the Repos but you have to add your own dictionaries, you can find dictionaries on [StarDict's site ]("http://stardict.sourceforge.net/Dictionaries.php")or [here.]("http://xdxf.revdanica.com/down/index.php") In the latter you must select the StarDict format on the drop-down list. But I don't use this so I don't know much about installing dictionaries in it


[*][Fantasdic]("http://www.gnome.org/projects/fantasdic/") This use the DICT protocol like the gnome-dictionary. Again I don't use this tho it looks like a good program :)
[/LIST]

---

### Post by meho_r on 2008-02-23
> **ronb94 said:**
> Thanks i'll try it but how do I convert the babylon dics to the stardict?

No need for conversion in StarDict v3. Just download dics and extract them in StarDict dic folder (usually /usr/share/stardict/dic)

---

### Post by gollum2000 on 2008-03-03
I don't have "Advanced settings" in the "Add Dictionary Source" panel. o.O

---

### Post by y-lee on 2008-03-03
> **gollum2000 said:**
> I don't have "Advanced settings" in the "Add Dictionary Source" panel. o.O

That doesn't make alot of sense, what version of Ubuntu are you using? 

try in the terminal

```
gnome-dictionary
```


and see if you have it there. If not what version of the dictionary do you have, see in menu help--> about.

---

### Post by gollum2000 on 2008-03-05
> **y-lee said:**
> That doesn't make alot of sense, what version of Ubuntu are you using? 

try in the terminal

```
gnome-dictionary
```


and see if you have it there. If not what version of the dictionary do you have, see in menu help--> about.
:)
I'm not a total newbie, I've reinstalled gnome-utils on my Gutsy 64bit, installed gnome-dictionary 2.20.0.1, but in either case there's no Advanced settings in Add Sources.
Help document says (section 4.2) nothing about advanced settings but it is present in figure 5.
In "Add Dictionary Source" window I have  "Dictionaries" and "Strategies" also. See the image attached.

Maybe 64bit and 32bit version are different? :/

---

### Post by MrKlister on 2008-04-30
> **gollum2000 said:**
> :)
I'm not a total newbie, I've reinstalled gnome-utils on my Gutsy 64bit, installed gnome-dictionary 2.20.0.1, but in either case there's no Advanced settings in Add Sources.
Help document says (section 4.2) nothing about advanced settings but it is present in figure 5.
In "Add Dictionary Source" window I have  "Dictionaries" and "Strategies" also. See the image attached.

Maybe 64bit and 32bit version are different? :/

I have the 32bit version and I also miss the advanced option so that ain't it. Really annoying. Someone who knows how to solve this problem?

I'm also using version 2.20.0.1 by the way.

---

### Post by LuCiAn0 on 2008-05-03
I'm using Hardy and there's no advance setting in my dictionary :(

gnome-dictionary-applet 2.20.0.1

:confused::confused:

---

### Post by Dafydd on 2008-05-08
I'm using Stardict. With version 3 and above you can also use converted Babylon dictionaries. That would solve your problems about Hebrew, Russian, English and French. Just download from:

[http://reciteword.sourceforge.net/stardict/babylon.php](http://reciteword.sourceforge.net/stardict/babylon.php)

Install Stardict (via Synaptic).

Also right click on the tar files and extract. Then move them to /usr/share/stardict/dic

Restart Stardict.

---

### Post by Dlizard on 2008-05-18
Total newbye using Hardy. No advanced settings in Add Dictionary Source either. What should I do?!

---

### Post by Aeroclub on 2008-05-23
Same here.

---

### Post by marciowb on 2008-07-17
There is [Stardict]("http://stardict.sourceforge.net"). Try it and love it! It's fantastic! Better than Babylon. Belive me.
If you need some help to full install it or its TTS or glossaries, see tips at: [http://www.marciowb.net/blog/2008/07...a-linux-para-o](http://www.marciowb.net/blog/2008/07...a-linux-para-o)

Regards,
Marcio Wesley Borges
[http://www.marciowb.net/blog/](http://www.marciowb.net/blog/)

---

### Post by cheep50 on 2008-07-20
> **Dafydd said:**
> 
Install Stardict (via Synaptic).

Also right click on the tar files and extract. Then move them to /usr/share/stardict/dic

Restart Stardict.

I have installed stardict 3.01 . And i have downloaded the databases : stardict-dictd_anh-viet-2.4.2.tar.bz2 . but i can not move and Paste it to /usr/share/stardict/dic . Please help me . thanks a lots .

---

