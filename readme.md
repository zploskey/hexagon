
<h1 align="center">
  <a href="http://hexagonkt.com">
    <img alt="Hexagon" src="hexagon_site/assets/tile-small.png" />
  </a>
  <br>
  Hexagon
</h1>

<h4 align="center">The atoms of your platform</h4>

<p align="center">
  <a href="https://travis-ci.org/hexagonkt/hexagon">
    <img
      src="https://img.shields.io/travis/hexagonkt/hexagon.svg?colorA=0073BB&style=flat-square" 
      alt="Travis CI" />
  </a>
  <a href="https://codecov.io/gh/hexagonkt/hexagon">
    <img
      src="https://img.shields.io/codecov/c/github/hexagonkt/hexagon.svg?colorA=0073BB&style=flat-square"
      alt="Codecov" />
  </a>
  <a href="https://bintray.com/jamming/maven/hexagon_core/_latestVersion">
    <img
      src="https://img.shields.io/bintray/v/jamming/maven/hexagon_core.svg?colorA=0073BB&style=flat-square"
      alt="Bintray" />
  </a>
</p>

<p align="center">
  <a href="https://travis-ci.org/hexagonkt/hexagon">
    Quick Start
  </a>
  |
  <a href="https://codecov.io/gh/hexagonkt/hexagon">
    Guides
  </a>
  |
  <a href="https://bintray.com/jamming/maven/hexagon_core/_latestVersion">
    API Reference
  </a>
  |
  <a href="https://bintray.com/jamming/maven/hexagon_core/_latestVersion">
    Community
  </a>
</p>

---

Hexagon is a microservices framework that doesn't follow the flock. It is written in [Kotlin] and
aims to implement the [Microservice Chassis Pattern] for a given platform. It takes care of:

* HTTP routing and HTML templates.
* Serialization and storage of domain classes.
* Asynchronous communication through events.
* Task scheduling using Cron expressions.

The purpose of the project is to provide a microservices framework with the following priorities
(in order):

1. Simple to use
2. Easily hackable
3. Be small

[Microservice Chassis Pattern]: http://microservices.io/patterns/microservice-chassis.html

## Getting Started

You can write a [Gradle] project from scratch (Gradle 3 or newer is required):

`build.gradle`:

```groovy
plugins {
    id 'org.jetbrains.kotlin.jvm' version '1.1.4-2'
}

apply plugin: "kotlin"
apply plugin: "application"

mainClassName = 'HelloKt'

repositories {
    jcenter ()
}

dependencies {
    compile ("com.hexagonkt:server_jetty:0.21.0")
}
```

`src/main/kotlin/Hello.kt`:

```kotlin
import com.hexagonkt.server.*
import com.hexagonkt.server.jetty.*

fun main(vararg args: String) {
    serve(JettyServletEngine()) {
        get("/hello/{name}") { "Hello ${request["name"]}!" }
    }
}
```

Now you can run the service with `gradle run` and view the results at:
[http://localhost:2010/hello/world](http://localhost:2010/hello/world)

[Lazybones]: https://github.com/pledbrook/lazybones
[Gradle]: https://gradle.org/

## Further Resources

* [Service Life Cycle]: provide helpers to create, build and package your services.
* [HTTP]: Web routing and filters. It is handled like the [Sinatra] Ruby framework.
* [Serialization]: helper methods to serialize/deserialize `data classes` using different formats.
* [Storage]: utilities to persist Kotlin objects into [MongoDB] collections.
* [Events]: support asynchronous communication with events through the [RabbitMQ] message broker.
* [Configuration]: allow the configuration of the engine by using YAML files.
* [Scheduling]: supports the execution of tasks periodically using Cron expressions.
* [Templates]: allow the service to render results using [Pebble] or [kotlinx.html].
* [Testing]: Hexagon adds utilities to ease the testing of its services.

[Sinatra]: http://sinatrarb.com
[Pebble]: http://www.mitchellbosecke.com/pebble/home
[kotlinx.html]: https://github.com/Kotlin/kotlinx.html

[Service Life Cycle]: http://hexagonkt.com/life_cycle.html
[HTTP]: http://hexagonkt.com/rest.html
[Serialization]: http://hexagonkt.com/serialization.html
[Storage]: http://hexagonkt.com/storage.html
[Events]: http://hexagonkt.com/events.html
[Configuration]: http://hexagonkt.com/configuration.html
[Templates]: http://hexagonkt.com/templates.html
[Scheduling]: http://hexagonkt.com/scheduling.html
[Testing]: http://hexagonkt.com/testing.html

## Status

**DISCLAIMER**: The project status is beta. Use it at your own risk. There are some modules not
started yet (ie: service registry) and the API is subject to change any time prior to release 1.0.

Performance is not the primary goal, but it is taken seriously. You can check performance numbers
in the [TechEmpower Web Framework Benchmarks](https://www.techempower.com/benchmarks)

This is the coverage grid:

[![CoverageGrid]][Coverage]

[CoverageGrid]: https://codecov.io/gh/hexagonkt/hexagon/branch/master/graphs/icicle.svg
[Coverage]: https://codecov.io/gh/hexagonkt/hexagon
[Kotlin]: http://kotlinlang.org
[RabbitMQ]: http://www.rabbitmq.com
[MongoDB]: https://www.mongodb.com

## Contribute

Refer to the [contributing.md](contributing.md) file for detailed information about Hexagon's
development.

TODO Project board

TODO Slack channel

Eventually I will thank all [contributors], but now it's just [me].

[contributors]: https://github.com/hexagonkt/hexagon/graphs/contributors
[me]: https://github.com/jaguililla

## License

The project is licensed under the [MIT License](license.md).
