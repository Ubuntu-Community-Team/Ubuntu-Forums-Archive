---
title: "Polygenic Calc command error: touch: cannot touch '.command.trace': Permission denied"
date: 2023-07-22
forum: General Help
---

### Post by hectorfp on 2023-07-22
[SIZE=4]Hi. I hope to get some help or suggestions. Have no experience and only installed Ubuntu for trying to run and use pgsc_calc for personal use on Ubuntu 22.04.2 that I installed for the first time on a new ssd drive.

Installed docker engine and docker desktop, created key and account to logging. It seems to be installed correctly although I have not made any specific test. Next installed nextflow. Used online guides provided by them and also some youtube tutorials for reference.

Here is the reference websites for pgsc_calc
[https://www.pgscatalog.org/](https://www.pgscatalog.org/)
[https://pgsc-calc.readthedocs.io/en/latest/index.html#credits](https://pgsc-calc.readthedocs.io/en/latest/index.html#credits)
[https://pgsc-calc.readthedocs.io/en/latest/getting-started.html](https://pgsc-calc.readthedocs.io/en/latest/getting-started.html)

There they posted information regarding how it works and how to install.

Tried this on the terminal.

**nextflow run pgscatalog/pgsc_calc --help**

It displayed correctly. Tried the next test and it did not work.

**nextflow run pgscatalog/pgsc_calc -profile test,docker**

It displays messages in red

**ERROR~Error executing process > 'PGSCATALOG_PGSCALC:PGSCALC:DOWNLOAD_SCOREFILES ([pgs_id:PGS002786, pgp_id:, trait_efo:])'**
[/SIZE][SIZE=4]
Further down it says:

**Command error: touch: cannot touch '.command.trace': Permission denied**[/SIZE]

[IMG]https://i.ibb.co/10qqxDQ/Screenshot-from-2023-07-22-11-08-19.png[/IMG]



[SIZE=4]I then created a csv sheet with the details for my own VCF file to test. And the result I believe is the same as with the previous test:

[/SIZE][IMG]https://i.ibb.co/h7BppXv/Screenshot-from-2023-07-22-12-35-35.png[/IMG]

[IMG]https://i.ibb.co/xJVPRCc/Screenshot-from-2023-07-22-12-35-58.png[/IMG][SIZE=4]

Since docker and nextflow seemed to be installed correctly and I am inexperienced with installing and running programs I am afraid to try too many things I don't understand that could modify the system or programs in a way that could cause other errors I might not be able to fix. pgsc_calc does not seem to be a widely used program that an average expert or experienced user with ubuntu, docker, and nextflow might know about and work with. But maybe its not different from other programs using docker and nextflow.

I was hoping that maybe somebody could help with some assistance in trying a possible solution. I believe that it could even be a very simple fix. I am willing to try anything at my own risk or provide any information, even personal or access to files or systems in the hopes of getting this to work for me.

If somebody could also learn how to use this calculator correctly by learning about the settings and files I would also be willing to pay a fee for further assistance. I want to be able to caculate any polygenic score provided by the calculators database using the publications and traits directory using my own personal whole genome sequencing VCF file and learning how to get and view the results presented in a way I can use.

Thank you.[/SIZE]

---

