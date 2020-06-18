-   Create the files primes.py and test\_primes.py

        touch primes.py test_primes.py

-   Write tests for the is\_prime method. Look at the contract!

    -   Negative, 0, and 1 are known to be not prime. Write a test for that.

            def test_prime_negative():
                assert not is_prime(-124387921)
                assert not is_prime(-1000)
                assert not is_prime(-3)

            def test_prime_zero():
                assert not is_prime(0)

            def test_prime_one():
                assert not is_prime(1)

    -   More interesting tests are anything above 1. Write tests for that.

            def test_prime_primes():
                assert is_prime(2)
                assert is_prime(89)
                assert is_prime(514229)

            def test_prime_composites():
                assert not is_prime(2)
                assert not is_prime(100)
                assert not is_prime(514230)

-   Run the tests, they will fail!

        pytest

-   This is expected behavior. We have written our tests, but the functions 
    under test have not even been written yet!

-   Let's start writing some actual code.

        def is_prime(num):
            if num < 0:
                return False
            elif num == 0:
                return False
            elif num == 1:
                return False
            else:
                return True

-   This definitely won't work, but let's just prove to ourselves that some
    of our tests are actually good now.

        pytest

-   We're still "red" because we haven't handled any of the interesting stuff!
    Let's fix that.

        def is_prime(num):
            if num < 0:
                return False
            elif num == 0:
                return False
            elif num == 1:
                return False
            else:
                # Iterate over values between 2 and num. If num mod val == 0, then
                # num can't be prime
                for i in range(2, num):
                    if num % i == 0:
                        return False

                # If we get here, 1 and num are the only factors!
                return True

-   That's all it should take to validate is\_prime. Is it the fastest code? No, but
    at least it's something.

        pytest

-   This puts us into Green! Good job!