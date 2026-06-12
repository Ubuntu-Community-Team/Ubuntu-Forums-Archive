---
title: "LibreOffice_ofx files"
date: 2017-07-01
forum: General Help
---

### Post by dee119 on 2017-07-01
:)  Hi - I wonder if anyone could help on a small problem I have.

I am using ubuntu 16.04

I need to download statements from my bank which come in the
form of microsoft .ofx files.

Have tried to convert into Linux files so that they would be presentable as statements,
but do not have the expertise to do this.

Any help, advice would be much appreciated.

Dee

---

### Post by vasa1 on 2017-07-01
If [http://file.org/extension/ofx](http://file.org/extension/ofx) is correct, there isn't anything non-Windows :(

If you're downloading, aren't there options for pdf, csv, html, etc?

---

### Post by gsahli on 2017-07-01
There are several programs available that import .ofx files.
[http://www.junauza.com/2013/01/best-finance-software-for-ubuntu.html](http://www.junauza.com/2013/01/best-finance-software-for-ubuntu.html)

---

### Post by vasa1 on 2017-07-01
> **gsahli said:**
> There are several programs available that import .ofx files.
[http://www.junauza.com/2013/01/best-finance-software-for-ubuntu.html](http://www.junauza.com/2013/01/best-finance-software-for-ubuntu.html)
Thanks!

OP may like GnuCash:> GnuCash is also the first free software application to support the OFX (Open Financial Exchange) protocol that many banks and financial services are starting to use.

---

### Post by dee119 on 2017-07-01
:) Hi and thank you everyone that replied to my question.

Sorry I have not come back to you sooner, but just arrived home.

Will study all your answers and report back which has been successful for me.

Once again, many thanks for your input it is much appreciated.

Dee

---

### Post by oldfred on 2017-07-01
I use Kmymoney & directly import ofx files or qfx files (as ofx). 

There are also python ofx converters, but then you need to know a little python to make your data usable in whatever format you may want.

---

### Post by dee119 on 2017-07-04
):P Hi again -  have been trying to fix my problem with you help, but
         struggling a bit at the moment.

As stated previously, I am trying to download my bank statement ( Nat, UK) which will
only let me download in microsoft .ofx files.   

When I try and save them after the download,  there is nothing in ubuntu 16.04 that 
will let me see the bank statement in it's original form.

Can you tell me if I have to get an apt or download some software to convert this
.ofx file into something ubuntu can read.

If so,  what file extension should I be looking for.

Thanks for looking and any input you can help with,  as you can see I am not that
up to speed yet with Linux.

Thank you - Dee

---

### Post by vasa1 on 2017-07-04
Have you installed GnuCash? That was one of the suggestions.```
sudo apt-get update
```followed by
```
sudo apt-get install gnucash
```

---

### Post by gsahli on 2017-07-04
> **dee119 said:**
> 
As stated previously, I am trying to download my bank statement ( Nat, UK) which will
only let me download in microsoft .ofx files.   

When I try and save them after the download,  there is nothing in ubuntu 16.04 that 
will let me see the bank statement in it's original form.


I think this is a misunderstanding. .ofx files contain transactions only. You won't ever be able to see the bank statement in original form. This type of file is for people who want to keep a running total of all the transactions in an account. If you want to see the original statement, the bank probably offers a .pdf file download (All my accounts have that option).

---

### Post by dee119 on 2017-07-05
:) Hi again - thanks to all for your input.

Have downloaded #gnucash and installed,  but sadly it is not what I require.

Thank you #gsahli as you have understood what I need.    All that I wanted was a copy of
my bank statement, so will try again to get a .pdf file of the said statement.

I think that the misunderstanding came from me as I probably did not explain what 
I wanted properly.  Now I have learned a little will try again to get my statement.

Thank you everyone for your patience and input.

Many thanks  - Dee

.

---

