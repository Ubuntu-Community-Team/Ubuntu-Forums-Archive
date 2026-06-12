---
title: "How do I sign a file with my smartcard on Ubuntu 20.10?"
date: 2020-12-29
forum: General Help
---

### Post by quinta65 on 2020-12-29
I own a Dell latitude E7240 running Ubuntu 20.10 with a smartcard reader (broadcom 5880) and a smartcad with a qualified certificate which I want to use to digitally sign files.

Cardpeek correctly sees the reader and the smartcard.

While previously I had no problems under Windows, I have found no usable app to sign files in Ubuntu.

Any suggestion  ?

thanks!, s.

---

### Post by #&amp;thj^% on 2020-12-29
IJDK but this might shed some light: [http://manpages.ubuntu.com/manpages/focal/man1/signtool.1.html#name](http://manpages.ubuntu.com/manpages/focal/man1/signtool.1.html#name)

---

### Post by quinta65 on 2020-12-30
thanks for posting
I cannot make any sense out of it.. 
:-(
I will keep studying and digging...

---

### Post by #&amp;thj^% on 2020-12-30
Maybe as an easier alternative, I have to use [DocuSign]("https://en.wikipedia.org/wiki/DocuSign"), which is a free web app (for single signatures). It also serves as a (hopefully) trusted third party.
> DocuSign, Inc. is an American company headquartered in San Francisco, California that allows organizations to manage electronic agreements. As part of the DocuSign Agreement Cloud, DocuSign offers eSignature, a way to sign electronically on different devices. DocuSign claims it has over 475,000 customers and hundreds of millions of users in more than 180 countries. Signatures processed by DocuSign are compliant with the US ESIGN Act. and the European Union's eIDAS regulation, including EU Advanced and EU Qualified Signatures.

Brief How To: [https://support.docusign.com/en/articles/How-do-I-sign-a-DocuSign-document-Basic-Signing](https://support.docusign.com/en/articles/How-do-I-sign-a-DocuSign-document-Basic-Signing)

---

### Post by quinta65 on 2021-01-09
thanks

I solved with a signing software from [https://www.bit4id.com/en/](https://www.bit4id.com/en/)

docusign mantains the documents on their servers, which in some cases is a  nice to have, but in others one might want to keep their own documents  on their own computers.. 
Furthermore, it has not a comparable legal status to state issued smartcards in Europe.

In Europe we have a regulation, eIDAS, that says that a digital signature has the same legal effects of a handwritten one, under some conditions.
(the regulation allows also for a remote online signing, but I already own a smartcard...)

In Italy we have more than 20 trust service providers issuing digital signatures and (as an order of magnitude)  several 10s of millions of signatures issued.
[https://www.agid.gov.it/piattaforme/firma-elettronica-qualificata/prestatori-di-servizi-fiduciari-attivi-in-italia](https://www.agid.gov.it/piattaforme/firma-elettronica-qualificata/prestatori-di-servizi-fiduciari-attivi-in-italia)
Some are issued for internal purposes, eg. for relations between a company (for example a bank) and their customers, some for general purposes.

A document signed with a signature issued by an accredited trust service provider has legal validity throughout Europe.
When issuing a digital signature the trust service provider verifies the identity of the person requesting it with a strict procedure.
Some of them offer a remote online verification, for example 
[https://www.pec.it/acquista-firma-digitale-remota.aspx](https://www.pec.it/acquista-firma-digitale-remota.aspx)
[https://www.firma.infocert.it/prodotti/firma-digitale.php#](https://www.firma.infocert.it/prodotti/firma-digitale.php#)
[https://www.firmacerta.it/firma-digitale-remota.php](https://www.firmacerta.it/firma-digitale-remota.php)

---

