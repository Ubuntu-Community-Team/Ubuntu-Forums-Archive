---
title: "installing SIPp IMS Benchmark on Ubuntu"
date: 2012-12-25
forum: General Help
---

### Post by domt on 2012-12-25
Good day,

I am currently trying to install SIPp IMS Benchmark on my PC.  I installed GSL, PerlXML and Gnu Plot. But when i execute the make rmtl the following error comes:

make OSNAME=Linux MODELNAME=i686 -C rmt
make[1]: Entering directory `/home/techdep/ims_bench/rmt'
make OSNAME=`uname|sed -e "s/CYGWIN.*/CYGWIN/"` MODELNAME=`uname -m|sed "s/Power Macintosh/ppc/"` rmt_tst
make[2]: Entering directory `/home/techdep/ims_bench/rmt'
gcc   -D__LINUX -pthread -D__3PCC__       -I. -I/opt/openssl/include -I/usr/include -I/usr/include/c++/4.6  -c -o RmtParm.o RmtParm.cpp
In file included from RmtParm.hpp:24:0,
                 from RmtParm.cpp:21:
RmtDefs.hpp:55:88: error: ‘ptrdiff_t’ was not declared in this scope
RmtDefs.hpp:55:88: note: suggested alternatives:
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:156:28: note:   ‘std::ptrdiff_t’
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:156:28: note:   ‘std::ptrdiff_t’
RmtDefs.hpp:55:97: error: template argument 3 is invalid
In file included from /usr/include/c++/4.6/iterator:61:0,
                 from RmtDefs.hpp:24,
                 from RmtParm.hpp:24,
                 from RmtParm.cpp:21:
/usr/include/c++/4.6/bits/stl_iterator_base_types.h: In instantiation of ‘std::iterator_traits<Rmt::iterator_for_sized<Rmt::RmtParm> >’:
/usr/include/c++/4.6/bits/stl_algo.h:4427:41:   instantiated from ‘_IIter std::find_if(_IIter, _IIter, _Predicate) [with _IIter = Rmt::iterator_for_sized<Rmt::RmtParm>, _Predicate = Rmt::RmtParm::CheckIdPred]’
RmtParm.cpp:78:89:   instantiated from here
/usr/include/c++/4.6/bits/stl_iterator_base_types.h:166:53: error: no type named ‘iterator_category’ in ‘class Rmt::iterator_for_sized<Rmt::RmtParm>’
/usr/include/c++/4.6/bits/stl_iterator_base_types.h:168:53: error: no type named ‘difference_type’ in ‘class Rmt::iterator_for_sized<Rmt::RmtParm>’
/usr/include/c++/4.6/bits/stl_iterator_base_types.h:169:53: error: no type named ‘pointer’ in ‘class Rmt::iterator_for_sized<Rmt::RmtParm>’
/usr/include/c++/4.6/bits/stl_iterator_base_types.h:170:53: error: no type named ‘reference’ in ‘class Rmt::iterator_for_sized<Rmt::RmtParm>’
In file included from /usr/include/c++/4.6/algorithm:63:0,
                 from RmtParmList.hpp:26,
                 from RmtParm.hpp:25,
                 from RmtParm.cpp:21:
/usr/include/c++/4.6/bits/stl_algo.h: In function ‘_IIter std::find_if(_IIter, _IIter, _Predicate) [with _IIter = Rmt::iterator_for_sized<Rmt::RmtParm>, _Predicate = Rmt::RmtParm::CheckIdPred]’:
RmtParm.cpp:78:89:   instantiated from here
/usr/include/c++/4.6/bits/stl_algo.h:4427:41: error: no matching function for call to ‘__iterator_category(Rmt::iterator_for_sized<Rmt::RmtParm>&)’
/usr/include/c++/4.6/bits/stl_algo.h:4427:41: note: candidate is:
/usr/include/c++/4.6/bits/stl_iterator_base_types.h:202:5: note: template<class _Iter> typename std::iterator_traits::iterator_category std::__iterator_category(const _Iter&)
make[2]: *** [RmtParm.o] Error 1
make[2]: Leaving directory `/home/techdep/ims_bench/rmt'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/techdep/ims_bench/rmt'
make: *** [rmtl] Error 2


Can someone please help me to solve this?

---

