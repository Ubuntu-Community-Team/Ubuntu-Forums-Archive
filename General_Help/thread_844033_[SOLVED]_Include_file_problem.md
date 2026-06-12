---
title: "[SOLVED] Include file problem"
date: 2008-06-29
forum: General Help
---

### Post by ceclauson on 2008-06-29
Hello!

I'm trying to program an application in C++ that uses the libxml++ API, but am having an include file problem, which is really embarrassing for me, because if you'd asked me a week ago, I would have told you that I was a pro at this.

The header file for libxml++ is libxml++/libxml++.h.  I have a line in my code that includes this, and the preprocessor finds it.  This header then includes a number of other headers which go on to include more headers pertaining to libxml++, and this seems to happen fine.

However, one of these headers has the line:

```

#include <glibmm/ustring.h>

```

And this causes a compilation error; the compiler complains that it can't find this header.  However, the header file is on my system in /usr/include/glibmm/ustring.h, which is where I thought the compiler would look.

So it seems that my understanding of how gpp looks up header files isn't as complete as I thought.  Any ideas?

Anything would be appreciated.

Thanks,
Cooper

---

### Post by HalPomeranz on 2008-06-29
Actually it sounds like you've got everything right.  Could there be another reason that /usr/include/glibmm/ustring.h isn't readable-- like permissions on the file or something?  Can you post the g++ command-line that's generating the compile error along with the exact error output?

---

### Post by ceclauson on 2008-06-30
Here's the output:

```

ceclauson@ceclauson-laptop:~/Desktop/programming/libxml$ gpp test.cpp

/* node.h
 * libxml++ and this file are copyright (C) 2000 by Ari Johnson, and
 * are covered by the GNU Lesser General Public License, which should be
 * included with libxml++ as the file COPYING.
 */


// -*- C++ -*-

/* internal_error.h
 *
 * Copyright (C) 2002 The libxml++ development team
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Library General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Library General Public License for more details.
 *
 * You should have received a copy of the GNU Library General Public
 * License along with this library; if not, write to the Free
 * Software Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 */


// -*- C++ -*-

/* exception.h
 *
 * Copyright (C) 2002 The libxml++ development team
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Library General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Library General Public License for more details.
 *
 * You should have received a copy of the GNU Library General Public
 * License along with this library; if not, write to the Free
 * Software Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 */


libxml++/exceptions/exception.h:26: error: Requested include file not found
ceclauson@ceclauson-laptop:~/Desktop/programming/libxml$ 

```

but I figured out what was wrong, I was using gpp when I usually use g++.  I don't really know why there's a difference, but it works with g++.

Thanks so much for your reply!

Cooper

---

