---
title: "XML validation help"
date: 2005-06-27
forum: General Help
---

### Post by v79 on 2005-06-27
(If this is the wrong forum, apologies).

I'm writing an application to output an XML file with a specific DTD. I don't know much about XML... I am trying to check that my XML files are valid and conform to the DTD. I understand that xmllint can check this for me, but I don't really understand the output much.

If I type:
$ xmllint --dtdvalid [http://www.editeur.org/onix/2.1/reference/onix-international.dtd](http://www.editeur.org/onix/2.1/reference/onix-international.dtd) onix.xml

I get my XML file, then the following error messages...

onix.xml:4: element Header: validity error : Element Header content does not follow the DTD, expecting (((FromEANNumber , FromSAN? , SenderIdentifier* , FromCompany?) | (FromSAN , SenderIdentifier* , FromCompany?) | (SenderIdentifier+ , FromCompany?) | FromCompany) , FromPerson? , FromEmail? , ToEANNumber? , ToSAN? , AddresseeIdentifier* , ToCompany? , ToPerson? , MessageNumber? , MessageRepeat? , SentDate , MessageNote? , DefaultLanguageOfText? , DefaultPriceTypeCode? , DefaultCurrencyCode? , DefaultLinearUnit? , DefaultWeightUnit? , DefaultClassOfTrade?), got (SentDate FromCompany FromPerson MessageNote )

<< snip >>

OK, so my XML header is invalid. But what does this mean? What do the various ?, * and + symbols mean? I presume that | is an or operator - does this mean that there are several different valid ways of writing a valid header? 

man xmllint tells me how to run the program, but not how to understand the output. Google isn't helping much either!

Can anyone here?

Liam

---

