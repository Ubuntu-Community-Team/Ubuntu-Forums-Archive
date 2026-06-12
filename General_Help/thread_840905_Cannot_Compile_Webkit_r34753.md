---
title: "Cannot Compile Webkit r34753"
date: 2008-06-25
forum: General Help
---

### Post by derubermensch on 2008-06-25
Ran apt-get -u build-dep libwebkitgtk1d prior to configuration and captured all neccessary sources.  Fails to make due to:
> make[1]: *** No rule to make target `WebCore/xml/XMLHttpRequestProgressEvent.cpp', needed by `WebCore/xml/libWebCore_la-XMLHttpRequestProgressEvent.lo'.  Stop.

Any help?  Or could someone suggest a recent revision that builds successfully?

---

### Post by mempman on 2008-06-26
There seems to be something wrong with the make file possibly.  make is trying to make the target XMLHttpRequestProgressEvent.cpp, but there are no rules to make it....below is a basic format for an entry in a make file.

```

# Comments use the hash symbol
target: dependencies
	command 1
	command 2
          .
          .
          .
	command n

```

---

