---
title: "Issues installing “MoNoise”"
date: 2020-03-20
forum: General Help
---

### Post by mthch on 2020-03-20
[SIZE=2][COLOR=#242729]Dear All

I wanted to install monoise on my environment ([https://bitbucket.org/robvanderg/monoise/src/master/README.md](https://bitbucket.org/robvanderg/monoise/src/master/README.md))
[/COLOR]
[COLOR=#242729]I followed the steps, which are outlined on the page:
[/COLOR][INDENT]cd monoise/src
icmbuild >  mkdir ../data
cd ../data
curl [www.robvandergoot.com/data/monoise/en.tar.gz]("http://www.robvandergoot.com/data/monoise/en.tar.gz") | tar xvz
cd ../src 
echo "new pix comming tomoroe" | ./tmp/bin/binary -r ../data/en/chenli -m RU -b -C -t -d ../data/en[/INDENT]

[COLOR=#242729]However, I am running into the following issue:[/COLOR][INDENT]echo "new pix comming tomoroe" | ./tmp/bin/binary -r ../data/en/chenli -m RU -b -C -t -v -d ../data/en
Loading: ../data/en/w2v.bin
Loading: ../data/en/w2v.bin.cache
Loading: ./../data/en/aspell-model
Loading: ../data/en/twitter.ngr.bin
Loading: ../data/en/wiki.ngr.bin
Loading: ../data/en/aspell
Loading: ../data/en/chenli.forest.
Segmentation fault (core dumped)[/INDENT]

[COLOR=#242729]At first, I thought this might be related to a memory issue and assigned 32 GB RAM to my virtual machine. However, the same error occurred. 
[/COLOR]
[COLOR=#242729]Do you have any input what the issue could be?
[/COLOR]
[COLOR=#242729]Thank you and Best Regards[/COLOR][/SIZE]

---

