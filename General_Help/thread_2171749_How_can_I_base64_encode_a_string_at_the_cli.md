---
title: "How can I base64 encode a string at the cli"
date: 2013-09-01
forum: General Help
---

### Post by sefs on 2013-09-01
I know I can go 

```

echo 'somestring' | base64

```

But the thing is my string can contain single or double quotes so the above does not work.

Is there a way to do it?

Thanks.

---

### Post by steeldriver on 2013-09-01
Have you tried enclosing the string with double quotes, and escaping any other double quotes within it?

```
$ echo "string \"with quotes\" and 'quotes'"
string "with quotes" and 'quotes'

```

If you are passing it to base64, you may want to use the echo -n option so it doesn't encode the trailing newline

```

$ echo "string \"with quotes\" and 'quotes'" | base64
c3RyaW5nICJ3aXRoIHF1b3RlcyIgYW5kICdxdW90ZXMnCg==
$ 
$ echo -n "string \"with quotes\" and 'quotes'" | base64
c3RyaW5nICJ3aXRoIHF1b3RlcyIgYW5kICdxdW90ZXMn

```

---

### Post by sefs on 2013-09-01
> **steeldriver said:**
> Have you tried enclosing the string with double quotes, and escaping any other double quotes within it?

```
$ echo "string \"with quotes\" and 'quotes'"
string "with quotes" and 'quotes'

```

If you are passing it to base64, you may want to use the echo -n option so it doesn't encode the trailing newline

```

$ echo "string \"with quotes\" and 'quotes'" | base64
c3RyaW5nICJ3aXRoIHF1b3RlcyIgYW5kICdxdW90ZXMnCg==
$ 
$ echo -n "string \"with quotes\" and 'quotes'" | base64
c3RyaW5nICJ3aXRoIHF1b3RlcyIgYW5kICdxdW90ZXMn

```

I found a easy way using stdin.
If I just type base64 at prompt, then I can paste the string there for base64 to read from stdin and then hit ctrl+D once or twice and it gives me the encoding.

Thanks for the reply.

---

