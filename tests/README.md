# Tests

This folder contains your tests.

Currently, there's only the setup for unit tests with [AVA](https://github.com/avajs/ava).

Example:

```JavaScript

// You must explicitly import the AVA module in each test file.
import test from 'ava';

// These data files are not included in the current project.
// If you want to run a working test, you can clone and run the tests
// in this repo: https://github.com/rootasjey/backwards.
import * as consumables from '../public/assets/data/consumables.json';
import * as heroes      from '../public/assets/data/heroes.json';
import * as units       from '../public/assets/data/unitsClasses.json';
import * as weapons     from '../public/assets/data/weapons.json';

import { unitsFactory } from '../src/logic/unitsFactory';

// The actual test
test("A unit's battle stats are numbers", async (assert) => {
  const createUnit = unitsFactory({
    dataConsummables  : consumables,
    dataHeroes        : heroes,
    dataUnits         : units,
    dataWeapons       : weapons,
  });

  const emilie = createUnit('emilie');

  Object.entries(emilie.getBattleStats())
    .map(([, value]) => {
      // If the following assertion is true for each value,
      // the test passes. Otherwise it fails.
      assert.true(typeof value === 'number'); }
    );
});

```

To learn more about how to write tests: [AVA documentation](https://github.com/avajs/ava/blob/master/docs/01-writing-tests.md).
