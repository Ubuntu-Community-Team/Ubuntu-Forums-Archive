---
title: "Evolution and Exchange 2003"
date: 2005-06-08
forum: General Help
---

### Post by thebasard on 2005-06-08
I'm hoping someone can help me.  I know that there are a few bugs with Evolution and its Exchange connector with respect to calendaring and address books on the Exchange server but I thought I'd post this querey anyhow to see if someone else had this same issue and a resolution.

Up until today, I had not gotten this error.  I've been using Evolution with the Exchange connector - version 2.2.1.1 - for about a month with some bugs but it has been usable for the most part.

Today I started getting the following error when attempting to respond to a meeting request sent by another Exchange user:

[B]Error while performing operation.

Could not send message.
This might mean that your account is over quota..[/B]

I'm the Exchange admin and we have no quotas in place at this time.  What gives???

Anyone else seen this same error and have a fix or workaround?

Thanks in advance,
thebasard

---

### Post by hotani on 2007-05-01
I have the same problem. It only happens on one machine accessing my exchange account. Other machines running evolution-exchange in Feisty, same versions of everything, are fine.

A fix would be lovely. The messages do get sent, but the error is irritating.

---

### Post by dcstar on 2007-05-01
> **hotani said:**
> I have the same problem. It only happens on one machine accessing my exchange account. Other machines running evolution-exchange in Feisty, same versions of everything, are fine.

A fix would be lovely. The messages do get sent, but the error is irritating.

Evolution is using the WEBDAV (I think) protocol with Exchange, you'd need to see the "raw" data flowing between the two systems to see if there is a difference between the machines that work versus the ones that don't.

It may be better to use the inbuilt tools to report a bug and let the experts ask you for more details.

---

### Post by hotani on 2007-05-04
fixed this by re-creating my exchange account and deleting the old one.

---

