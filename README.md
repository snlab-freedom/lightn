Light-weight Network IDE
========================

I'm going to start an independent project to deliver a light-weight IDE for SDN high-level programming.

Why Light-weight?
-----------------

There are several projects ([NetIDE] etc.) to produce the NetDevOp environment based on some popular but complicated IDE frameworks such as Eclipse and IntelliJ. Our team also made some attempts. [DevOpen] is our first work. It is based on [Cloud9] online IDE framework. But in its life of half a year, we have found many shortcomings on it. And we realize that Cloud9 may not be a good solution for our requirements. We have started another two projects (an IntelliJ-based SDN programming plugin and a web-based NetDevOp dashboard) to make better user experience.

But we just want things easier. If we can deliver a very simple tool to maintain the whole lifecycle (or more flexible workflow) for NetDevOp without the complex IDE framework, that will be a very fancy work. We are going to discard any existing popular IDE framework but just deliver **a single command-line tool**. It is independent of any IDE framework. In other words, you can make it work with any IDE framework if you want.

How to Achieve It?
------------------

We just deliver a **single command-line tool** to achieve this goal. And in the first alpha release, it only covers the following features:

- CRUD a profile of an existing SDN controller from a built-in database.
- Network application workflow:
    - Create a network control application from the template.
    - Build an application.
    - Deploy an application into an SDN controller.
- Host a temporal web server for real-time monitoring and open the web browser to display it.
- Network test environment:
    - Docker/vagrant based test SDN controller.
    - Docker/vagrant based virtual network engine.
    - General purpose test framework for network scenario.

Initial Design
--------------

    Usage: lw-netdev <command> [<args>]

    These commands will be supported by the first alpha release:
       controller  Manage profiles of SDN controllers (add/list/info/update/delete)
          add         Add a profile for an SDN controller
          list        List all profiles of SDN controllers
          info        Show the detail information of an SDN controller
          update      Update the profile of an SDN controller
          delete      Remove a profile from the database
       app         Maintain the lifecycle of network application project (create/build/deploy/test)
          create      Create a network application project from the template
          build       Build the application
          deploy      Deploy the application to an SDN controller
          test        Run offline test for the application
       monitor     Start a web server to monitor the state of a controller
       test        Commands for a general purpose network test framework
          define      Define a test case from the template
          run         Run test cases from a profile or configuration file
          report      Generate the test report
       utils       Some utility tools
          tracetree   Visualize a trace tree from a file or a connected Maple controller

  [NetIDE]: https://github.com/fp7-netide/
  [DevOpen]: https://github.com/snlab/Devopen/wiki/Overview
  [Cloud9]: https://c9.io/
