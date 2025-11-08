class Solution {
    public int minimumOneBitOperations(int n) {
        return helper(n);
    }
    
    private int helper(int n) {
        if (n == 0) return 0;

        // find highest set bit k
        int k = 31 - Integer.numberOfLeadingZeros(n);
        
        int mask = 1 << k;

        // formula: 2^(k+1) - 1 - f(n XOR 2^k)
        return (1 << (k + 1)) - 1 - helper(n ^ mask);
    }
}
