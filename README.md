leveldb
=======

A key-value store

Authors: Sanjay Ghemawat (sanjay@google.com) and Jeff Dean (jeff@google.com)

The code under this directory implements a system for maintaining a
persistent key/value store.

See doc/index.html for more explanation.
See doc/impl.html for a brief overview of the implementation.

The public interface is in include/*.h.  Callers should not include or
rely on the details of any other header files in this package.  Those
internal APIs may be changed without warning.

Guide to header files:

include/db.h
    Main interface to the DB: Start here

include/options.h
    Control over the behavior of an entire database, and also
    control over the behavior of individual reads and writes.

include/comparator.h
    Abstraction for user-specified comparison function.  If you want
    just bytewise comparison of keys, you can use the default comparator,
    but clients can write their own comparator implementations if they
    want custom ordering (e.g. to handle different character
    encodings, etc.)

include/iterator.h
    Interface for iterating over data. You can get an iterator
    from a DB object.

include/write_batch.h
    Interface for atomically applying multiple updates to a database.

include/slice.h
    A simple module for maintaining a pointer and a length into some
    other byte array.

include/status.h
    Status is returned from many of the public interfaces and is used
    to report success and various kinds of errors.

include/env.h
    Abstraction of the OS environment.  A posix implementation of
    this interface is in util/env_posix.cc

include/table.h
include/table_builder.h
    Lower-level modules that most clients probably won't use directly
