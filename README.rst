backport_ipaddress
==================

.. image:: https://badge.fury.io/py/backport_ipaddress.png
    :target: http://badge.fury.io/py/backport_ipaddress

.. image:: https://travis-ci.org/sk-/backport_ipaddress.png?branch=master
    :target: https://travis-ci.org/sk-/backport_ipaddress

.. image:: https://coveralls.io/repos/sk-/backport_ipaddress/badge.png?branch=master
    :target: https://coveralls.io/r/sk-/backport_ipaddress?branch=master

backport_collections is a backport of Python 3's ``ipaddress`` module for Python 2.6 and Python 2.7.
It is based on the backport of Søren Løvborg (https://bitbucket.org/kwi/py2-ipaddress/).

What is backported?
-------------------

The ``ipaddress`` module.

Usage
-----

To use it just import the module ``ipaddress`` as you would in Python 3.
Example::

    import ipaddress

Differences
-----------

Given that there is no real ``bytes`` types in Python 2, we are using ``bytearray``, which is a
mutable version of ``bytes`` and in Python 2, has fewer methods.

So if in Python 3 you would do::

    ipaddress.ip_address(b'\x00\x00\x00\x00')

with this port you need to do::

    ipaddress.ip_address(bytearray('\x00\x00\x00\x00'))

Missing
-------

One thing that is missing and could be important for performance is the
``lru_cache`` for many of the methods. ``functools`` in Python 2 does not have
such decorator. Maybe in the future I will backport that method as well.

License
-------

The Python Software Foundation License.

Changes
-------

* v0.1 (15/08/2014): Synced to revision http://hg.python.org/cpython/rev/15bfb82194fa