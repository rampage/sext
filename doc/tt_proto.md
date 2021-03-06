Module tt_proto
===============


<h1>Module tt_proto</h1>

* [Description](#description)
* [Function Index](#index)
* [Function Details](#functions)


Bare-bones Tokyo Tyrant interface library.



__Behaviours:__ [`gen_server`](gen_server.md).

__Authors:__ Ulf Wiger ([`ulf.wiger@erlang-consulting.com`](mailto:ulf.wiger@erlang-consulting.com)).

<h2><a name="description">Description</a></h2>



 
This is an example to illustrate the use of Sortable EXernal Term (sext)  
encoding.



[Tokyo Tyrant](http://1978th.net/tokyotyrant/) (TT) is an add-on
to [Tokyo Cabinet](http://1978th.net/tokyocabinet/), adding  
support for concurrent and remote access to Tokyo Cabinet (TC) through a  
TCP socket interface. TC supports storage of variable-length byte strings  
as key-value pairs. The storage type can either be RAM-only or disk, and  
either hash table or B-tree.



Using sext-encoded terms in combination with TT's B-tree storage, it is
possible to store very large amounts of data on disk while honoring the
Erlang Term ordering semantics. Using the `sext:prefix/1` function, it is  
also possible to perform efficient range queries.

Tokyo Tyrant is easy to install and get running. This module does not show
how that is done, nor does it automate the task of starting a TT server.


<h2><a name="index">Function Index</a></h2>



<table width="100%" border="1" cellspacing="0" cellpadding="2" summary="function index"><tr><td valign="top"><a href="#get-2">get/2</a></td><td>Looks up Key in the database TT.</td></tr><tr><td valign="top"><a href="#keys-2">keys/2</a></td><td>Performs a prefix search in database TT based on Prefix.</td></tr><tr><td valign="top"><a href="#mget-2">mget/2</a></td><td>Fetches multiple objects from the database TT.</td></tr><tr><td valign="top"><a href="#open-2">open/2</a></td><td>Connects to a running Tokyo Tyrant database server.</td></tr><tr><td valign="top"><a href="#put-3">put/3</a></td><td>Inserts a <code>{Key,Value}</code> tuple in the database TT.</td></tr></table>


<a name="functions"></a>


<h2>Function Details</h2>


<a name="get-2"></a>


<h3>get/2</h3>





<tt>get(TT, Key::term()) -> {ok, Value} | {error, Reason}</tt>



Looks up Key in the database TT.
Returns `{ok,Value}` if found, otherwise `{error,Reason}`.
<a name="keys-2"></a>


<h3>keys/2</h3>





<tt>keys(TT, Prefix) -> {ok, Keys} | {error, Reason}</tt>



Performs a prefix search in database TT based on Prefix.
For details on Prefix, @see sext:prefix/1.
<a name="mget-2"></a>


<h3>mget/2</h3>





<tt>mget(TT, Keys::[term()]) -> {ok, [{K, V}]} | {error, Reason}</tt>



Fetches multiple objects from the database TT.
All objects matching the list of keys will be returned. If no objects match,
the return value will be `{ok, []}`.
<a name="open-2"></a>


<h3>open/2</h3>





<tt>open(Name, Opts) -> {ok, pid()}</tt>* `Opts = [Opt]`
* `Opt = {regname, atom()} | {port, integer()}`




Connects to a running Tokyo Tyrant database server.
The default port, 1978, will be used unless another port is specified.
If the `regname` option is present, the Tokyo Tyrant proxy process will
register itself under that name, and the registered name can be used as
an alias when accessing the database.
<a name="put-3"></a>


<h3>put/3</h3>





<tt>put(TT, Key::term(), Value::term()) -> ok | {error, Reason}</tt>



Inserts a `{Key,Value}` tuple in the database TT.

_Generated by EDoc, Nov 23 2010, 08:23:29._