UPGRADE FROM 3.x to 4.0
=======================

DependencyInjection
-------------------

 * Using unsupported configuration keys in YAML configuration files raises an
   exception.

 * Using unsupported options to configure service aliases raises an exception.

Form
----

 * The `choices_as_values` option of the `ChoiceType` has been removed.

Serializer
----------

 * The ability to pass a Doctrine `Cache` instance to the `ClassMetadataFactory`
   class has been removed. You should use the `CacheClassMetadataFactory` class
   instead.

Yaml
----

 * Removed support for passing `true`/`false` as the second argument to the
   `parse()` method to trigger exceptions when an invalid type was passed.

   Before:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', true);
   ```

   After:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', YAML::PARSE_EXCEPTION_ON_INVALID_TYPE);
   ```

 * Removed support for passing `true`/`false` as the third argument to the
   `parse()` method to toggle object support.

   Before:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', false, true);
   ```

   After:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', Yaml::PARSE_OBJECT);
   ```

 * Removed support for passing `true`/`false` as the fourth argument to the
   `parse()` method to parse objects as maps.

   Before:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', false, false, true);
   ```

   After:

   ```php
   Yaml::parse('{ "foo": "bar", "fiz": "cat" }', Yaml::PARSE_OBJECT_FOR_MAP);
   ```

 * Removed support for passing `true`/`false` as the third argument to the `dump()` methods to toggle object support.

   Before:

   ```php
   Yaml::dump(array('foo' => new A(), 'bar' => 1), 0, 0, false, true);
   ```

   After:

   ```php
   Yaml::dump(array('foo' => new A(), 'bar' => 1), 0, 0, false, Yaml::DUMP_OBJECT);
   ```

 * The `!!php/object` tag to indicate dumped PHP objects was removed in favor of
   the `!php/object` tag.