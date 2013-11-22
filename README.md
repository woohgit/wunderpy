wunderpy
========

[![Build Status](https://travis-ci.org/bsmt/wunderpy.png)](https://travis-ci.org/bsmt/wunderpy)

The goal of this project is to make [Wunderlist's](https://wunderlist.com) private and undocumented API less private and better documented, while also providing a python client implementation. I've explained how I figured out the API in a blog post [here](http://bsmt.me/blog/2013/03/02/reverse-engineering-the-wunderlist-api/), in case anyone is curious or wants to contribute.

You can read the documentation at [readthedocs.](https://wunderpy.readthedocs.org/en/latest/)

Disclaimer
----------

In no way is this project near complete or perfect. There are a lot of things that can be done better, especially design-wise, that I'm trying to fix as I learn more. Things are liable to change or break unexpectedly.

Example
-------

	from datetime import datetime
	from wunderpy import Wunderlist

	w = Wunderlist()
	w.login("username", "password")
	w.update_lists()  # you have to run this first, before you do anything else

	w.add_list("test")  # make a new list called "test"
	
	due = datetime.now().isoformat()
	w.add_task("test wunderpy", list="test", note="a note",
			   due_date=due, starred=True)  # add a task to it
	w.complete_task("test wunderpy", "test")  # complete it
	w.delete_task("test wunderpy", "test")  # and delete it

	w.delete_list("test")  # and delete the list

Building the Docs
-----------------

Chances are, you're looking for information on how to use the API. I'm in the process of documenting everything in wunderpy. Information on the API, as well as the classes provided by wunderpy are documented with sphinx.

To generate the documentation:

    cd docs
    make html # other options are available
    # look in the docs/build/html dir for the documentation

Running Tests
-------------

I'm working on writing tests for everything.

If you want to run said tests, make sure you have nose and nose-testconfig installed. Next, setup an ini config somewhere (I use the project root) that looks something like this:

    [login]
    email = test@email.web
    password = password

Now you can run the tests from the project root like this:

    nosetests --tc-file test_config.ini

License
-------

The MIT License (MIT)

Copyright (c) 2013 bsmt

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

